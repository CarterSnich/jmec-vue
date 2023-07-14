<script setup lang="ts">
import { useStorage } from '@vueuse/core'
import { ref } from 'vue'

const themeSwitcher = ref(null)
const lightMode = useStorage('LIGHTMODE', true)
</script>

<template scoped>
  <div id="theme-switcher">
    <label>
      <input type="checkbox" ref="themeSwitcher" v-model="lightMode" />
      <span></span>
    </label>
  </div>
</template>

<style>
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

/*
  ===========================================
                  LIGHT MODE
  ===========================================
 */

.light #theme-switcher > label {
  background-position: right;
}

.light #theme-switcher span:before {
  content: '';
}

/*
  ===========================================
                RESPONSIVE
  ===========================================
 */

/* Small devices (landscape phones, less than 768px) */
@media (max-width: 767.98px) {
  #theme-switcher {
    top: 0.75rem;
    right: 0.75rem;
    bottom: unset;
    left: unset;
  }
}
</style>
