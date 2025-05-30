<template>
  <!-- Start Screen -->
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

  <!-- Level 1: Projects -->
  <ProjectSection />

  <!-- Level 2: About Me -->
  <AboutSection />

  <!-- Final Boss: Contact -->
  <ContactSection />
</template>

<script setup>
// Import the new level components
import ProjectSection from './components/ProjectSection.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'

// Scroll to Projects when clicking Start
const goToProjects = () => {
  const el = document.getElementById("projects");
  if (el) el.scrollIntoView({ behavior: "smooth" });
};
</script>
