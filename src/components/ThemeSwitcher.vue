<script setup lang="ts">
let lightMode: boolean = false

function themeSwitch() {
  lightMode = !lightMode
  console.log(document.getElementById('app'))
  document.getElementById('app')?.classList.toggle('light', lightMode)
  localStorage.setItem('LIGHTMODE', `${lightMode}`)
}
</script>

<template>
  <div id="theme-switcher">
    <label>
      <input type="checkbox" ref="themeSwitcher" v-on:change="themeSwitch" />
      <span></span>
    </label>
  </div>
</template>

<style scoped>
#theme-switcher {
  position: fixed;
  bottom: 0.75rem;
  left: 0.75rem;
}

#theme-switcher > label {
  position: relative;
  padding: 0.25rem;
  height: calc(12px + 2rem);
  width: calc(12px + 2rem);

  display: grid;
  place-content: center;

  border-radius: 50%;
  background-image: linear-gradient(90deg, var(--night) 50%, var(--platinum) 50%);
  background-size: 200%;
  background-position: left;
  background-repeat: no-repeat;

  transition: background-position 0.3s ease-in-out;
}

#theme-switcher input {
  display: none;
}

#theme-switcher span {
  mix-blend-mode: difference;
}

#theme-switcher span::before {
  content: '';
  font-size: calc(12px + 1rem);
}
</style>
