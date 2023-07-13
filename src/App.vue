<script setup lang="ts">
import { ref, toRef, type Ref } from 'vue'
import { vIntersectionObserver } from '@vueuse/components'
import { setInterval, clearInterval } from 'timers-browserify'

import ScrollSpy from './components/ScrollSpy.vue'
import ThemeSwitcher from './components/ThemeSwitcher.vue'
import HomeSection from './components/HomeSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'

const main: Ref = ref(null)
const homeSection: Ref = ref(null)
const skillsSection: Ref = ref(null)
const aboutSection: Ref = ref(null)
const contactSection: Ref = ref(null)

const currentSection: Ref<string> = ref('')
</script>

<template>
  <ScrollSpy :current-section="toRef(currentSection)" />

  <main ref="main">
    <HomeSection
      ref="homeSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => {
          if (isIntersecting) {
            currentSection = 'home'
            homeSection.$refs.myName.classList.add('animate')
          }
        },
        { root: main }
      ]"
    />
    <SkillsSection
      ref="skillsSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => {
          if (isIntersecting) {
            currentSection = 'skills'
            skillsSection.$refs.skills.classList.add('animate')
          }
        },
        { root: main }
      ]"
    />
    <AboutSection
      ref="aboutSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => {
          if (isIntersecting) {
            currentSection = 'about'

            const aboutMeHidden = aboutSection.$refs.pre1
            const aboutMeVisible = aboutSection.$refs.pre2

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
        { root: main }
      ]"
    />
    <ContactSection
      ref="contactSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => {
          currentSection = 'contact'
        },
        { root: main }
      ]"
    />
  </main>

  <ThemeSwitcher />
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
