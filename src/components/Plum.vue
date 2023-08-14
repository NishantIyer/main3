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
const interactiveRadius = 80
const interactiveRadiusSquared = interactiveRadius * interactiveRadius

interface Dot {
  x: number
  y: number
  radius: number
  originalRadius: number
  angle: number
}

function createDot(): Dot {
  const x = Math.random() * size.width
  const y = Math.random() * size.height
  const radius = Math.random() * 3 + 1
  const originalRadius = radius
  const angle = Math.random() * Math.PI * 2

  return { x, y, radius, originalRadius, angle }
}

function updateDots(): void {
  dots.forEach((dot) => {
    dot.x += Math.cos(dot.angle) * 0.5
    dot.y += Math.sin(dot.angle) * 0.5

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
    ctx.fillStyle = '#333' // Dark gray color
    ctx.shadowColor = '#000' // Black shadow
    ctx.shadowBlur = 15
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
      dot.radius = dot.originalRadius + 3 // Enlarge the dot
      dot.angle += 0.1 // Spin the dot
    } else if (dot.radius > dot.originalRadius) {
      dot.radius -= 0.5 // Gradually return to original size
    }
  })
}

onMounted(() => {
  const canvas = el.value!
  const ctx = canvas.getContext('2d')!
  canvas.width = size.width
  canvas.height = size.height

  for (let i = 0; i < 20; i++) {
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
