<template>
  <!-- Start Screen -->
  <section class="game-landing fade-in">
    <div class="twinkle-layer"></div> <!-- ✨ Twinkling stars layer -->

    <div class="hud">
      <h1 class="game-title">
        <span class="name">Sara McHattie</span>
      </h1>

      <p class="game-subtitle typewriter">
        VR & Game Dev <span class="divider">|</span> Mobile Apps <span class="divider">|</span> Web Projects<span class="cursor">|</span>
      </p>

      <button class="start-button" @click="goToProjects">▶ Start</button>
    </div>
  </section>

  <!-- Level 1: Projects -->
  <ProjectSection />

  <!-- Level 2: About Me -->
  <AboutSection />

  <!-- Final Boss: Contact -->
  <ContactSection />
</template>

<script setup>
// Components
import ProjectSection from './components/ProjectSection.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'

// Scroll behavior
const goToProjects = () => {
  const el = document.getElementById("projects");
  if (el) {
    el.scrollIntoView({ behavior: "smooth" });
  }
};
</script>
