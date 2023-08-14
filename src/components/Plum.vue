<template>
  <div class="background">
    <canvas ref="el" :width="size.width" :height="size.height" />
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, reactive } from 'vue'
import { useWindowSize } from '@vueuse/core'

const el = ref<HTMLCanvasElement | null>(null)
const size = reactive(useWindowSize())

let dots: Dot[] = []
const interactiveRadius = 50
const interactiveRadiusSquared = interactiveRadius * interactiveRadius

interface Dot {
  x: number
  y: number
  radius: number
  color: string
  dx: number
  dy: number
  originalRadius: number
  angle: number
}

function createDot(): Dot {
  const x = Math.random() * size.width
  const y = Math.random() * size.height
  const radius = Math.random() * 3 + 1
  const originalRadius = radius
  const color = 'rgba(240, 240, 240, 0.8)' // Dim white with transparency
  const dx = (Math.random() - 0.5) * 2
  const dy = (Math.random() - 0.5) * 2
  const angle = Math.random() * Math.PI * 2

  return { x, y, radius, color, dx, dy, originalRadius, angle }
}

function updateDots(): void {
  dots.forEach((dot) => {
    dot.x += dot.dx
    dot.y += dot.dy
    dot.angle += 0.01 // Increase the angle for rotation

    if (dot.x + dot.radius > size.width || dot.x - dot.radius < 0) {
      dot.dx = -dot.dx
    }

    if (dot.y + dot.radius > size.height || dot.y - dot.radius < 0) {
      dot.dy = -dot.dy
    }
  })
}

function drawDots(ctx: CanvasRenderingContext2D): void {
  ctx.clearRect(0, 0, size.width, size.height)
  dots.forEach((dot) => {
    ctx.save()
    ctx.translate(dot.x, dot.y)
    ctx.rotate(dot.angle) // Rotate the dot
    ctx.beginPath()
    ctx.arc(0, 0, dot.radius, 0, Math.PI * 2)
    ctx.fillStyle = dot.color
    ctx.shadowColor = 'rgba(0, 0, 0, 0.5)' // Darker shadow color with transparency
    ctx.shadowBlur = dot.radius * 2 // Adjusted shadow blur
    ctx.fill()
    ctx.restore()
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

  window.addEventListener('mousemove', handleMouseMove)
  window.addEventListener('touchmove', handleTouchMove, { passive: true })
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
  background-color: #000000;
}

canvas {
  position: fixed;
  top: 0;
  left: 0;
}
</style>
