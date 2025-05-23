<template>
  <section class="game-landing">
    <div class="hud">
      <h1 class="game-title">
        <span class="name">Sara McHattie</span><span class="cursor">|</span>
      </h1>

      <p class="game-subtitle typewriter">
        VR & Game Dev <span class="divider">|</span> Mobile Apps <span class="divider">|</span> Web Projects
      </p>
      <button class="start-button" @click="goToProjects">▶ Start</button>
    </div>
  </section>

  <section id="projects" style="height: 100vh; background: #1e1e2f; color: white; display: flex; align-items: center; justify-content: center;">
    <h2>Level 1: Projects Coming Soon...</h2>
  </section>
</template>

<script setup>
const goToProjects = () => {
  const el = document.getElementById("projects");
  if (el) el.scrollIntoView({ behavior: "smooth" });
};
</script>
