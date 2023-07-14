<script setup lang="ts">
import { ref } from 'vue'
const aboutMe: string = `hello there!

i'm joe mar closa, a skilled software developer specializing in web development. my expertise includes html/css, javascript frameworks, php, and python. i also have experience in mobile app development. proficiency in writing automations with python and shell scripts. i leverage my linux expertise to create and manage servers for web servicing.

i'm passionate about building innovative solutions that push boundaries and deliver exceptional user experiences. let's collaborate and create remarkable software together!`

const pre1 = ref(null)
const pre2 = ref(null)
</script>

<template>
  <section id="about">
    <div class="about-me">
      <pre ref="pre1">{{ aboutMe }}</pre>
      <pre ref="pre2"></pre>
    </div>
    <div id="doc-dw-links">
      <a href="assets/resume.pdf" download> resume</a>
      <a href="assets/cv.pdf" download> cv</a>
      <a href="assets/biodata.pdf" download> biodata</a>
    </div>
  </section>
</template>

<style scoped>
section#about {
  display: grid;
  place-content: center;

  font-size: x-large;

  text-shadow: var(--shadow);

  transition: text-shadow 0.3s ease-in-out;
}

section#about > * {
  padding: 1.25rem;
}

div.about-me {
  display: grid;
  place-content: center;
  isolation: isolate;
}

div.about-me > pre {
  grid-column: 1 / -1;
  grid-row: 1 / -1;
  white-space: break-spaces;
  line-height: 1.75rem;
}

div.about-me > pre:first-child {
  color: transparent;
}

div.about-me > pre:nth-child(2) > span {
  border-right: 0.75rem solid var(--platinum); /* The typwriter cursor */
  animation: typing 1s steps(13, end), blink-caret 1s step-end infinite;
}

#doc-dw-links {
  display: flex;
  flex-direction: row;
}

#doc-dw-links > a {
  flex-grow: 1;
  text-align: center;

  color: inherit;
  text-decoration: none;

  background-image: var(--gradient-middle);
  background-size: 0%;
  background-position: center center;
  background-repeat: no-repeat;

  transition: all 0.3s ease-in-out;
}

#doc-dw-links > a:hover {
  color: var(--onyx);
  background-size: 100%;
}

@keyframes blink {
  0% {
    background-color: transparent;
  }

  20% {
    color: var(--onyx);
    background-color: var(--platinum);
  }

  40% {
    background-color: transparent;
  }

  60% {
    color: var(--onyx);
    background-color: var(--platinum);
  }

  80% {
    background-color: transparent;
  }

  100% {
    color: var(--onyx);
    background-color: var(--platinum);
  }
}

@keyframes blink-caret {
  from,
  to {
    border-color: var(--platinum);
  }
  50% {
    border-color: transparent;
  }
}

/*
  ===========================================
                  LIGHT MODE
  ===========================================
 */

.light section#about {
  text-shadow: var(--shadow-light);
}

/*
  ===========================================
                RESPONSIVE
  ===========================================
 */

/* X-Small devices (portrait phones, less than 576px) */
@media (max-width: 575.98px) {
  section#about {
    font-size: 4vw;
  }
}

/* Small devices (landscape phones, less than 768px) */
@media (max-width: 767.98px) {
  section#about {
    font-size: 4vw;
  }

  section#about > div > a:active {
    background-size: 100%;
    color: var(--onyx);
    mix-blend-mode: difference;
  }
}
</style>
