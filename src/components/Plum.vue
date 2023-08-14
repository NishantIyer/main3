<template>
  <div class="background">
    <canvas ref="el" :width="size.width" :height="size.height" @mousemove="handleMouseMove" />
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, reactive } from 'vue'
import { useWindowSize } from '@vueuse/core'

const el = ref<HTMLCanvasElement | null>(null)
const size = reactive(useWindowSize())

let dots: Dot[] = []
const interactiveRadius = 100
const interactiveRadiusSquared = interactiveRadius * interactiveRadius

interface Dot {
  x: number
  y: number
  startX: number
  startY: number
  radius: number
  originalRadius: number
  angle: number
  speed: number
}

function createDot(): Dot {
  const x = Math.random() * size.width
  const y = Math.random() * size.height
  const radius = Math.random() * 4 + 2
  const originalRadius = radius
  const angle = Math.random() * Math.PI * 2
  const speed = Math.random() * 1 + 0.5

  return { x, y, startX: x, startY: y, radius, originalRadius, angle, speed }
}

function updateDots(): void {
  dots.forEach((dot) => {
    dot.x += Math.cos(dot.angle) * dot.speed
    dot.y += Math.sin(dot.angle) * dot.speed

    if (dot.x + dot.radius > size.width || dot.x - dot.radius < 0) {
      dot.angle = Math.PI - dot.angle
    }

    if (dot.y + dot.radius > size.height || dot.y - dot.radius < 0) {
      dot.angle = -dot.angle
    }
  })
}

function drawDots(ctx: CanvasRenderingContext2D): void {
  ctx.clearRect(0, 0, size.width, size.height)
  dots.forEach((dot) => {
    ctx.save()
    ctx.translate(dot.x, dot.y)
    ctx.beginPath()
    ctx.arc(0, 0, dot.radius, 0, Math.PI * 2)
    ctx.fillStyle = '#444' // Darker gray color
    ctx.shadowColor = '#000' // Black shadow
    ctx.shadowBlur = 20
    ctx.fill()
    ctx.restore()
  })
}

function handleMouseMove(event: MouseEvent): void {
  const mouseX = event.pageX
  const mouseY = event.pageY

  dots.forEach((dot) => {
    const distanceSquared = (mouseX - dot.x) ** 2 + (mouseY - dot.y) ** 2
    if (distanceSquared < interactiveRadiusSquared) {
      const angle = Math.atan2(dot.y - mouseY, dot.x - mouseX)
      dot.x += Math.cos(angle) * 2 // Move away from mouse
      dot.y += Math.sin(angle) * 2 // Move away from mouse
      dot.radius = dot.originalRadius - 2 // Shrink the dot
    } else if (dot.radius < dot.originalRadius) {
      dot.radius += 0.5 // Gradually return to original size
      dot.x += (dot.startX - dot.x) * 0.02 // Return to initial x position
      dot.y += (dot.startY - dot.y) * 0.02 // Return to initial y position
    }
  })
}

onMounted(() => {
  const canvas = el.value!
  const ctx = canvas.getContext('2d')!
  canvas.width = size.width
  canvas.height = size.height

  for (let i = 0; i < 30; i++) {
    dots.push(createDot())
  }

  const animation = () => {
    updateDots()
    drawDots(ctx)
    requestAnimationFrame(animation)
  }

  animation()
})
</script>

<style scoped>
.background {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: -1;
  pointer-events: none;
  background-color: #000;
}

canvas {
  position: fixed;
  top: 0;
  left: 0;
}
</style>
