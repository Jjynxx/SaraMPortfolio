<template>
  <section id="contact" class="level-section">
    <h2 class="section-title">Final Boss: Contact</h2>
    <div class="contact-links">
      <a 
        href="https://github.com/Jjynxx" 
        target="_blank" 
        rel="noopener noreferrer" 
        class="contact-button"
      >
        GitHub
      </a>
      <a 
        href="https://www.linkedin.com/feed/?trk=guest_homepage-basic_nav-header-signin" 
        target="_blank" 
        rel="noopener noreferrer" 
        class="contact-button"
      >
        LinkedIn
      </a>
    </div>

    <!-- Proper Button for Back to Top -->
    <div class="section-buttons">
      <button class="nav-button" @click="scrollToTop">Back to Top ↑</button>
    </div>
  </section>
</template>

<script setup>
const scrollToTop = () => {
  console.log('Button clicked!'); // ✅ Debug log
  window.scrollTo({ top: 0, behavior: 'smooth' });
};
</script>

<style scoped>
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
  text-decoration: none; /* even for buttons */
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.nav-button:hover {
  background-color: var(--accent-purple);
  color: black;
  box-shadow: 0 0 15px var(--accent-purple);
}
</style>
