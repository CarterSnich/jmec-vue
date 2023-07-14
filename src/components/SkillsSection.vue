<script setup lang="ts">
import { ref } from 'vue'

const skills = ref(null)
</script>

<template>
  <section id="skills" ref="skills">
    <!-- FRONT-END -->
    <div class="skill-card">
      <div>
        <i>󰧨</i>
        <span>front-end</span>
      </div>
      <ul>
        <li>
          <i class="devicon-react-original"></i>
          react
        </li>
        <li>
          <i class="devicon-vuejs-plain"></i>
          vue.js
        </li>
      </ul>
    </div>

    <!-- BACK-END -->
    <div class="skill-card">
      <div>
        <i></i>
        <span>back-end</span>
      </div>
      <ul>
        <li>
          <i class="devicon-laravel-plain"></i>
          laravel
        </li>
        <li>
          <i class="devicon-flask-original"></i>
          flask
        </li>
        <li>
          <i class="devicon-express-original"></i>
          express.js
        </li>
        <li>
          <i class="devicon-nextjs-original"></i>
          next.js
        </li>
      </ul>
    </div>

    <!-- DATABASE -->
    <div class="skill-card">
      <div>
        <i>󰒋</i>
        <span>database</span>
      </div>
      <ul>
        <li>
          <i class="devicon-mysql-plain"></i>
          mySQL
        </li>
        <li>
          <i class="devicon-postgresql-plain"></i>
          postgreSQL
        </li>
        <li>
          <i class="devicon-mongodb-plain"></i>
          mongoDB
        </li>
      </ul>
    </div>

    <!-- MOBILE DEVELOPMENT -->
    <div class="skill-card">
      <div>
        <i>󰓷</i>
        <span>mobile <br />development</span>
      </div>
      <ul>
        <li>
          <i class="devicon-androidstudio-plain"></i>
          android studio
        </li>
        <li>
          <i class="devicon-flutter-plain"></i>
          flutter
        </li>
        <li>
          <i class="devicon-react-original"></i>
          react native
        </li>
      </ul>
    </div>

    <!-- LINUX -->
    <div class="skill-card">
      <div>
        <i></i>
        <span>linux</span>
      </div>
      <ul>
        <li>
          <i class="devicon-bash-plain"></i>
          bash
        </li>
        <li>
          <i class="devicon-apache-plain"></i>
          apache
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
@import url(https://cdn.jsdelivr.net/gh/devicons/devicon@v2.15.1/devicon.min.css);

section#skills {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  row-gap: 1.25rem;
  column-gap: 1.25rem;
}

section#skills.animate .skill-card {
  animation: appear-from-left 1s ease-in-out forwards;
}

section#skills.animate .skill-card:nth-child(2) {
  animation-delay: 100ms;
}

section#skills.animate .skill-card:nth-child(3) {
  animation-delay: 200ms;
}

section#skills.animate .skill-card:nth-child(4) {
  animation-delay: 300ms;
}

section#skills.animate .skill-card:nth-child(5) {
  animation-delay: 400ms;
}

.skill-card {
  position: relative;

  flex-shrink: 0;
  flex-grow: 0;

  display: grid;
  place-content: center;
  width: 30%;
  height: auto;

  border-radius: 1rem;

  color: inherit;
  text-decoration: none;
  text-align: center;
  white-space: nowrap;
  text-shadow: var(--shadow);

  filter: blur(8px);
  transform: translateX(-50%);

  transition: text-shadow 0.3s ease-in-out;
}

.skill-card > div {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-size: 2.25rem;
}

.skill-card > div > i {
  font-size: 3.25rem;
}

.skill-card > ul {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  display: flex;
  flex-direction: column;
  gap: 1rem;

  list-style-type: none;
  font-size: 2rem;

  opacity: 0;
}

.skill-card > ul > li {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 0.5rem;
}

.skill-card,
.skill-card * {
  transition: all 0.3s ease-in-out;
}

.skill-card:hover {
  box-shadow: inset var(--shadow), var(--shadow);
}

.skill-card:hover > div {
  opacity: 0;
}

.skill-card:hover > ul {
  opacity: 1;
}

@keyframes appear-from-left {
  from {
    filter: blur(8px);
    transform: translateX(-50%);
  }

  to {
    filter: blur(0px);
    transform: translateX(0%);
  }
}

/*
  ===========================================
                  LIGHT MODE
  ===========================================
 */

.light .skill-card {
  text-shadow: var(--shadow-light);
}

.light .skill-card:hover {
  background-color: var(--night-40);
}

/*
  ===========================================
                RESPONSIVE
  ===========================================
 */

@media (max-width: 767.98px) {
  section#skills {
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: flex-start;
    align-items: center;
    overflow: scroll;
    scroll-snap-type: x mandatory;
    padding: 2rem;

    /* hide scrollbar */
    scrollbar-width: none; /* For Firefox */
    -ms-overflow-style: none; /* For Internet Explorer and Edge */
  }

  /* hide scrollbar */
  section#skills::-webkit-scrollbar {
    display: none; /* For Chrome, Safari, and Opera */
  }

  div.skill-card {
    flex-grow: 1;
    width: calc(100% - 1rem);
    height: calc(100% - 16rem);
    box-shadow: inset var(--shadow), var(--shadow);
    background-color: rgba(13, 13, 13, 0.8);

    display: grid;
    place-content: center;
    gap: 5.25rem;

    pointer-events: none;
    scroll-snap-align: center;
  }

  div.skill-card > * {
    opacity: 1;
    position: static;
    transform: unset;
  }
}
</style>
