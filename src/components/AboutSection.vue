<template>
  <section id="about" class="level-section">
    <div class="about-box">
      <div class="about-text">
        <h2 class="about-title">About Me</h2>
        <img src="/images/portfolio_picture.jpg" alt="Portfolio Picture" class="profile-image" />
        <p>
          I am a software developer with a passion for VR and game development, supported by a strong 
          foundation in C++, C#, Java, and JavaScript. I have experience with full-stack web development 
          using HTML, CSS, and modern frameworks, and I am skilled in working with databases like MySQL, 
          PostgreSQL, and MongoDB.
        </p>
        <p>
          Through my background in software development and fitness, I’ve developed a blend of technical 
          expertise and soft skills like communication, problem-solving, and teamwork. Over the past few 
          years, I have expanded my skills to include VR and XR development, Unreal Engine, Unity, and 
          Blender, focusing on creating immersive experiences and efficient, scalable systems.
        </p>
        <p>
          Recently, I have also gained experience with mainframe technologies including COBOL, CICS, and 
          JCL — while valuable, my interests are primarily in modern web technologies, database engineering, 
          and the growing field of VR and XR applications.
        </p>
        <p>
          I am excited to apply my technical and creative skills to build innovative solutions and experiences, 
          particularly in the VR, gaming, and tech industries.
        </p>
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
  const el = document.getElementById("contact"); // 🟢 Make sure your Contact section has id="contact"
  if (el) {
    el.scrollIntoView({ behavior: "smooth" });
  }
};

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
};
</script>

