<script setup lang="ts">
import { type Ref } from 'vue'

defineProps<{
  currentSection: Ref
}>()
</script>

<template>
  <div id="scroll-spy">
    <ul>
      <li :class="{ active: currentSection.value === 'home' }">
        <a href="#home" data-target-id="home">home</a>
      </li>
      <li :class="{ active: currentSection.value === 'skills' }">
        <a href="#skills">skills</a>
      </li>
      <li :class="{ active: currentSection.value === 'about' }">
        <a href="#about">about</a>
      </li>
      <li :class="{ active: currentSection.value === 'contact' }">
        <a href="#contact">contact</a>
      </li>
    </ul>
  </div>
</template>

<style>
div#scroll-spy {
  display: grid;
  place-content: center;
  width: 3.25rem;

  background-image: linear-gradient(90deg, #00000000 0%, var(--night) 100%);

  transition: backdrop-filter 0.3s ease-in-out;
}

div#scroll-spy > ul {
  rotate: 90deg;

  display: flex;
  flex-direction: row;
  width: 100vh;

  list-style-type: none;
}

div#scroll-spy > ul * {
  transition: all 0.3s ease-in-out;
}

div#scroll-spy > ul > li {
  flex-grow: 1;
  height: 2.25rem;

  display: grid;
  place-content: center;
  justify-content: stretch;

  position: relative;
}

div#scroll-spy > ul > li.active::after {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);

  content: '';
  width: 0%;
  height: 2px;

  background-color: var(--platinum-80);
  box-shadow: 0px 0px 12px var(--platinum);

  animation: scroll-spy-link-active-indicator 0.3s ease-in-out forwards;
}

div#scroll-spy > ul > li > a {
  display: block;
  width: 100%;
  color: inherit;

  font-size: large;
  text-align: center;
  text-decoration: none;
}

div#scroll-spy > ul > li > a {
  background-image: var(--gradient-middle);
  background-size: 0%;
  background-position: center center;
  background-repeat: no-repeat;
}

div#scroll-spy > ul > li > a:hover {
  color: var(--onyx);
  background-size: 100%;
}

@keyframes scroll-spy-link-active-indicator {
  100% {
    width: calc(100% - 1rem);
  }
}
</style>
