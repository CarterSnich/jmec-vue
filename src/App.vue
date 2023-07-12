<script setup lang="ts">
import { ref } from 'vue'
import { vIntersectionObserver } from '@vueuse/components'
import { setInterval, clearInterval } from 'timers-browserify'

import ScrollSpy from './components/ScrollSpy.vue'
import ThemeSwitcher from './components/ThemeSwitcher.vue'
import HomeSection from './components/HomeSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'

const main = ref(null)
const homeSection = ref(null)
const skillsSection = ref(null)
const aboutSection = ref(null)
const contactSection = ref(null)
</script>

<template>
  <ScrollSpy />

  <main ref="main">
    <HomeSection
      ref="homeSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => {
          if (isIntersecting) $refs.homeSection.$refs.myName.classList.add('animate')
        },
        { main }
      ]"
    />
    <SkillsSection
      ref="skillsSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => {
          if (isIntersecting) $refs.skillsSection.$refs.skills.classList.add('animate')
        },
        { main }
      ]"
    />
    <AboutSection
      ref="aboutSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => {
          if (isIntersecting) {
            const aboutMeHidden = $refs.aboutSection.$refs.pre1
            const aboutMeVisible = $refs.aboutSection.$refs.pre2

            if (!aboutMeVisible.innerText) {
              let i = 0
              let interval = setInterval(() => {
                aboutMeVisible.innerText += aboutMeHidden.innerText[i]
                aboutMeVisible.innerHTML += `<span></span>`
                if (i >= aboutMeHidden.innerText.length - 1) {
                  clearInterval(interval)
                }
                ++i
              }, aboutMeHidden.innerText.length * 0.05)
            }
          }
        },
        { main }
      ]"
    />
    <ContactSection
      ref="contactSection"
      v-intersection-observer="[([{ isIntersecting }]) => {}, { main }]"
    />
  </main>

  <ThemeSwitcher v-on:click="" />
</template>

<style scoped>
main {
  flex-grow: 1;

  height: 100vh;
  isolation: isolate;
  scroll-snap-type: y mandatory;
  overflow-x: hidden;
  overflow-y: auto;

  /* hide scrollbar */
  scrollbar-width: none; /* For Firefox */
  -ms-overflow-style: none; /* For Internet Explorer and Edge */
}

/* hide scrollbar */
main::-webkit-scrollbar {
  display: none; /* For Chrome, Safari, and Opera */
}

main > section {
  height: 100vh;
  padding: 2.25rem;
  scroll-snap-align: center;
}
</style>
