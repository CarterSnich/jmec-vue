<script setup lang="ts">
import { ref } from 'vue'
import myImage from '../assets/img/me.jpg'

const myName = ref(null)
</script>

<template>
  <section id="home">
    <div class="me">
      <img :src="myImage" alt="me" />
    </div>
    <div class="intro">
      <div>
        <div class="bar"></div>
        <div class="my-name" ref="myName">
          <h1>joe mar closa</h1>
          <h1>joe mar closa</h1>
        </div>
        <p>software developer</p>

        <div id="links">
          <ul>
            <li><a href="#skills">skills</a></li>
            <li><a href="#about">about</a></li>
            <li><a href="#contact">contact</a></li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style>
section#home {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}

div.me {
  display: grid;
  place-content: center;
  position: relative;
  padding: 1rem;
  transition: filter 0.3s ease-in-out;
}

div.me > img {
  height: calc(100% - 1rem);
  width: calc(100% - 1rem);
  margin: auto;
  border-radius: 1rem;
  box-shadow: var(--shadow);

  transition: box-shadow 0.3s ease-in-out;
}

div.intro {
  align-self: stretch;
  display: grid;
  place-content: center;

  text-shadow: var(--shadow);
  transition: text-shadow 0.3s ease-in-out;
}

div.intro > div {
  position: relative;
}

div.intro > div > div.my-name {
  position: relative;
}

div.intro > div > div.my-name > h1:first-child {
  color: transparent !important;
  text-shadow: inherit;
  white-space: nowrap;
}

div.intro > div > div.my-name > h1:nth-child(2) {
  box-sizing: content-box;
  overflow: hidden;
  white-space: nowrap;
  position: absolute;
  text-shadow: none;
  width: 0%;
  top: 0;
  left: 0;
  border-right: 1.25rem solid var(--platinum);
}

div.intro > div > div.my-name.animate > h1:nth-child(2) {
  animation: typing 1s steps(13, end) forwards, blink-caret 1s step-end infinite;
}

div.intro > div > div.bar {
  position: absolute;
  border-radius: 1rem;
  background-color: var(--platinum);
  box-shadow: var(--shadow);
  height: 105%;
  width: 4px;
  top: 50%;
  left: -1rem;
  transform: translateY(-50%);
}

#links {
  margin-top: 1.25rem;
}

#links > ul {
  list-style-type: none;
  overflow: hidden;
  font-weight: bold;
  overflow: visible;
}

#links > ul > li {
  color: var(--platinum);
  background-image: linear-gradient(90deg, #dededeff 66%, #dedede00 100%);
  background-size: 0%;
  background-repeat: no-repeat;
  transition: all 0.3s ease-in-out;
}

#links > ul > li::before {
  content: '⋙ ';
}

#links > ul > li > a {
  color: inherit;
  text-decoration: none;
  mix-blend-mode: darken;
}

#links > ul > li:hover {
  color: var(--onyx);
  mix-blend-mode: difference;
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

@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 100%;
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
</style>
