<template>
  <div>
    <section id="navbar" style="font-family: 'Andalé Mono', monospace;">
      <nav class="navbar fixed-top navbar-expand-lg navbar-light navbar-fixed-top" style="background-color: #e3f2fd;">
        <div class="container-fluid px-5">
          <h1 class="navbar-brand mb-0 h1" style="font-weight: bold;" @click="scrollToSection('Welcome')">
            <i class="bi bi-playstation"></i> Thatthep Sataranaporn
          </h1>

          <div class="collapse navbar-collapse justify-content-end" id="navbarNav">
            <ul class="navbar-nav">
              <li class="nav-item">
                <a class="nav-link active" aria-current="page" @click="scrollToSection('Welcome')">
                  Welcome
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link" @click="scrollToSection('AboutMe')">
                  About
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link" @click="scrollToSection('Education')">
                  Education
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link" @click="scrollToSection('Record')">
                  Record
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link" @click="scrollToSection('Skills')">
                  Skills
                </a>
              </li>
            </ul>
          </div>
        </div>
      </nav>
    </section>

    <section id="Welcome" ref="Welcome">
      <Welcome />
    </section>

    <section id="AboutMe" ref="AboutMe">
      <AboutMe />
    </section>

    <section id="Hobbies">
      <TheHobbies />
    </section>

    <section id="Education" ref="Education">
      <Education />
    </section>

    <section id="Record" ref="Record">
      <RecordPage />
    </section>

    <section id="Skills" ref="Skills">
      <Skills />
    </section>
  </div>
</template>

<script>
import Welcome from "./components/Welcome.vue";
import AboutMe from "./components/AboutMe.vue";
import TheHobbies from "./components/TheHobbies.vue";
import Education from "./components/Education.vue";
import Skills from "./components/Skills.vue";
import RecordPage from "./components/RecordPage.vue";

export default {
  name: "App",
  components: {
    Welcome,
    AboutMe,
    TheHobbies,
    Education,
    Skills,
    RecordPage,
  },
  methods: {
    scrollToSection(sectionId) {
      const element = document.getElementById(sectionId);
      if (element) {
        element.scrollIntoView({ behavior: "smooth" });
      }
    },
  },
};
</script>

<style scoped>
.nav-link {
  position: relative;
  cursor: pointer;
}

.hover-icon {
  display: none;
  position: absolute;
  left: 100%;
  margin-left: 5px;
}

.nav-link:hover .hover-icon {
  display: inline-block;
}
</style>
