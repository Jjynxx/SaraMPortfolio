<template>
  <section class="game-landing fade-in">
    <!-- Galaxy Background Layer -->
    <div class="galaxy-layer"></div>

    <!-- Star Canvas -->
    <canvas id="starCanvas" class="star-canvas"></canvas>

    <div class="hud">
      <h1 class="game-title">
        <span class="name">Sara McHattie</span>
      </h1>

      <p class="game-subtitle typewriter">
        VR & Game Developer <span class="divider">|</span> Database Engineer <span class="divider">|</span> Web Developer<span class="cursor">|</span>
      </p>

      <button class="start-button" @click="goToProjects">▶ Start</button>
    </div>
  </section>

  <ProjectSection />
  <AboutSection />
  <ContactSection />
</template>

<script setup>
import { onMounted } from 'vue'
import ProjectSection from './components/ProjectSection.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'

const goToProjects = () => {
  const el = document.getElementById("projects");
  if (el) {
    el.scrollIntoView({ behavior: "smooth" });
  }
};

onMounted(() => {
  const canvas = document.getElementById('starCanvas');
  const ctx = canvas.getContext('2d');
  let width = window.innerWidth;
  let height = window.innerHeight;
  canvas.width = width;
  canvas.height = height;

  const colors = [
    'rgba(198, 172, 255, 0.8)',   // Soft purple
    'rgba(57, 255, 20, 0.7)',     // Faint lime green
    'rgba(173, 216, 230, 0.7)',   // Light blue
    'rgba(255, 255, 255, 0.9)',   // White
  ];

  const starCount = 150;
  const stars = Array.from({ length: starCount }, () => ({
    x: Math.random() * width,
    y: Math.random() * height,
    radius: Math.random() * 2 + 0.5,
    opacity: Math.random() * 0.5 + 0.5,
    delta: (Math.random() * 0.01 + 0.003),
    drift: (Math.random() * 0.4 + 0.1),
    color: colors[Math.floor(Math.random() * colors.length)],
  }));

  const shootingStars = [];

  function createShootingStar() {
    shootingStars.push({
      x: Math.random() * width,
      y: Math.random() * height / 2,
      length: Math.random() * 300 + 100,
      speed: Math.random() * 6 + 4, // More natural random speed
      opacity: 1,
      trailLengthDelta: Math.random() * 0.1 + 0.05, // Trail variation
    });
  }

  // Zoom pulse
  let zoom = 1;
  let zoomDirection = 1;
  function updateZoom() {
    zoom += 0.0003 * zoomDirection;
    if (zoom > 1.02 || zoom < 0.98) {
      zoomDirection *= -1;
    }
  }

  function drawStars() {
    ctx.save();
    ctx.setTransform(zoom, 0, 0, zoom, width / 2 * (1 - zoom), height / 2 * (1 - zoom));
    ctx.clearRect(0, 0, width, height);

    stars.forEach(star => {
      ctx.beginPath();
      ctx.globalAlpha = star.opacity;
      ctx.fillStyle = star.color;
      ctx.arc(star.x, star.y, star.radius, 0, Math.PI * 2);
      ctx.fill();

      star.opacity += star.delta;
      if (star.opacity >= 1 || star.opacity <= 0.5) {
        star.delta = -star.delta;
      }

      star.x -= star.drift;
      if (star.x < 0) {
        star.x = width;
        star.y = Math.random() * height;
      }
    });

    // Draw shooting stars with blur trails
    shootingStars.forEach((shootingStar, index) => {
      const grad = ctx.createLinearGradient(
        shootingStar.x,
        shootingStar.y,
        shootingStar.x + shootingStar.length,
        shootingStar.y + shootingStar.length * 0.2
      );
      grad.addColorStop(0, `rgba(255, 255, 255, ${shootingStar.opacity})`);
      grad.addColorStop(1, `rgba(255, 255, 255, 0)`);

      ctx.strokeStyle = grad;
      ctx.lineWidth = 2;
      ctx.beginPath();
      ctx.moveTo(shootingStar.x, shootingStar.y);
      ctx.lineTo(
        shootingStar.x + shootingStar.length,
        shootingStar.y + shootingStar.length * 0.2
      );
      ctx.stroke();

      shootingStar.x += shootingStar.speed;
      shootingStar.y += shootingStar.speed * 0.2;
      shootingStar.opacity -= shootingStar.trailLengthDelta;

      if (shootingStar.opacity <= 0) {
        shootingStars.splice(index, 1);
      }
    });

    ctx.restore();
    requestAnimationFrame(drawStars);
  }

  drawStars();

  setInterval(createShootingStar, 6000); // Shooting star every ~6 seconds

  // Parallax effect
  window.addEventListener('mousemove', (e) => {
    const parallaxX = (e.clientX - width / 2) * 0.00015;
    const parallaxY = (e.clientY - height / 2) * 0.00015;

    stars.forEach(star => {
      star.x += parallaxX;
      star.y += parallaxY;
    });
  });

  window.addEventListener('resize', () => {
    width = window.innerWidth;
    height = window.innerHeight;
    canvas.width = width;
    canvas.height = height;
  });

  function animate() {
    updateZoom();
    requestAnimationFrame(animate);
  }
  animate();
});
</script>
