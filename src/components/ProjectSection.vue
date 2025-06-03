<template>
  <section id="projects" class="level-section">
    <h2 class="section-title">Projects</h2>
    <div class="projects-container">
      <div class="project-card">
        <img src="/images/jynxflix.png" alt="JynxFlix Thumbnail" class="project-thumbnail" />
        <h3 class="project-title">JynxFlix Video Database</h3>
        <p class="project-description">
          A video database app that allows users to browse and search for videos, 
          built with a focus on smooth user experience and clean design.
        </p>
        <a href="https://github.com/Jjynxx/JynxFlix-VideoDatabase" target="_blank" class="project-button">View Project</a>
      </div>

      <!-- Coming Soon Placeholder -->
      <div class="project-card">
        <img src="/images/placeholder.png" alt="Coming Soon" class="project-thumbnail" />
        <h3 class="project-title">Coming Soon</h3>
        <p class="project-description">
          More exciting projects are on the way. Stay tuned!
        </p>
        <div class="project-button disabled">Coming Soon</div>
      </div>
    </div>

    <!-- Navigation Buttons -->
    <div class="section-buttons">
      <button class="nav-button" @click="goToNextLevel">Next Level ↓</button>
      <button class="nav-button" @click="scrollToTop">Back to Top ↑</button>
    </div>
  </section>
</template>

<script setup>
const goToNextLevel = () => {
  const el = document.getElementById("about"); // 🟢 Make sure your About section has id="about"
  if (el) {
    el.scrollIntoView({ behavior: "smooth" }); // 🎯 SIMPLER version!
  }
};

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
};
</script>


<style scoped>
.projects-container {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  justify-content: center;
}

.project-card {
  background-color: rgba(31, 27, 46, 0.9);
  border: 2px solid var(--accent-purple);
  border-radius: 12px;
  box-shadow: 0 0 15px var(--accent-purple);
  width: 300px;
  padding: 1.5rem;
  text-align: center;
  transition: transform 0.3s ease;
}

.project-card:hover {
  transform: scale(1.05);
}

.project-thumbnail {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 1rem;
}

.project-title {
  font-family: 'Press Start 2P', monospace;
  color: var(--accent-green);
  margin-bottom: 1rem;
}

.project-description {
  font-family: 'Rajdhani', sans-serif;
  color: var(--text-light);
  font-size: 1rem;
  margin-bottom: 1.5rem;
}

.project-button {
  background-color: transparent;
  border: 2px solid var(--accent-purple);
  color: var(--text-light);
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  text-decoration: none;
  font-family: 'Press Start 2P', monospace;
  transition: all 0.3s ease;
}

.project-button:hover {
  background-color: var(--accent-purple);
  color: black;
  box-shadow: 0 0 15px var(--accent-purple);
}

.project-button.disabled {
  opacity: 0.5;
  cursor: not-allowed;
  pointer-events: none;
}

/* Navigation Buttons */
.section-buttons {
  display: flex;
  justify-content: center;
  gap: 2rem;
  margin-top: 3rem;
}

.nav-button {
  background-color: transparent;
  border: 2px solid var(--accent-purple);
  color: var(--text-light);
  padding: 0.75rem 1.5rem;
  font-family: 'Press Start 2P', monospace;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
  text-transform: uppercase;
}

.nav-button:hover {
  background-color: var(--accent-purple);
  color: black;
  box-shadow: 0 0 15px var(--accent-purple);
}
</style>
