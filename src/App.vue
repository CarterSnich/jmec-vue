<script setup lang="ts">
import { ref, toRef, type Ref, watch, onMounted } from 'vue'
import { vIntersectionObserver } from '@vueuse/components'
import { setInterval, clearInterval } from 'timers-browserify'

import ScrollSpy from './components/ScrollSpy.vue'
import ThemeSwitcher from './components/ThemeSwitcher.vue'
import HomeSection from './components/HomeSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'
import { useStorage } from '@vueuse/core'

const main: Ref = ref(null)
const homeSection: Ref = ref(null)
const skillsSection: Ref = ref(null)
const aboutSection: Ref = ref(null)
const contactSection: Ref = ref(null)

const currentSection: Ref<string> = ref('')
const lightMode = useStorage('LIGHTMODE', false)

onMounted(() => {
  document.getElementById('app')?.classList.toggle('light', lightMode.value)
})

watch(lightMode, (newValue) => {
  document.getElementById('app')?.classList.toggle('light', newValue)
})

async function observer(isIntersecting: boolean, section: string) {
  if (isIntersecting) {
    currentSection.value = section

    switch (section) {
      case 'home':
        homeSection.value.$refs.myName.classList.add('animate')
        break

      case 'skills':
        skillsSection.value.$refs.skills.classList.add('animate')
        break

      case 'about':
        if (isIntersecting) {
          const aboutMeHidden = aboutSection.value.$refs.pre1
          const aboutMeVisible = aboutSection.value.$refs.pre2

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
        break
    }
  }
}
</script>

<template>
  <ScrollSpy :current-section="toRef(currentSection)" />

  <main ref="main">
    <HomeSection
      ref="homeSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => observer(isIntersecting, 'home'),
        { root: main }
      ]"
    />
    <SkillsSection
      ref="skillsSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => observer(isIntersecting, 'skills'),
        { root: main }
      ]"
    />
    <AboutSection
      ref="aboutSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => observer(isIntersecting, 'about'),
        { root: main }
      ]"
    />
    <ContactSection
      ref="contactSection"
      v-intersection-observer="[
        ([{ isIntersecting }]) => observer(isIntersecting, 'contact'),
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
