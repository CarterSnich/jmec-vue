<script setup lang="ts"></script>

<template>
  <section id="contact">
    <ul id="contact-links">
      <li>
        <a href="tel:+639619601674"> +63 (961) 960 1674</a>
      </li>
      <li>
        <a href="mailto:jmestreraclosa@gmail.com"> jmestreraclosa@gmail.com</a>
      </li>
      <li>
        <a href="#"> Joe Mar Closa</a>
      </li>
      <li>
        <a href="https://linkedin.com/in/joe-mar-c-8244b5135">󰌻 Joe Mar Closa</a>
      </li>
      <li>
        <a href="https://github.com/CarterSnich"> CarterSnich</a>
      </li>
    </ul>
  </section>
</template>

<style scoped>
section#contact {
  display: grid;
  place-content: center;
  justify-content: stretch;

  text-align: center;
  text-shadow: var(--shadow);
}

ul#contact-links {
  display: grid;
  gap: 1.25rem;
  list-style-type: none;
}

ul#contact-links > li > a {
  display: block;

  color: var(--platinum);
  text-decoration: none;
  outline: none;
  padding-inline: 1.25rem;

  background-image: var(--gradient-middle);
  background-size: 0%;
  background-position: center center;
  background-repeat: no-repeat;

  transition: all 0.3s ease-in-out, text-shadow 0.3s ease-in-out;
}

ul#contact-links > li > a:hover {
  color: var(--onyx);
  background-size: 100%;
}

/* 
  ===========================================
                  LIGHT MODE
  ===========================================
 */

.light section#contact {
  text-shadow: var(--shadow-light);
}

/* 
  ===========================================
                RESPONSIVE
  ===========================================
 */

/* X-Small devices (portrait phones, less than 576px) */
@media (max-width: 575.98px) {
  section#contact {
    font-size: 4vw;
  }
}

/* Small devices (landscape phones, less than 768px) */
@media (max-width: 767.98px) {
  section#contact {
    font-size: 4vw;
    white-space: nowrap;
  }
}

/* Large devices (desktops, 992px and up) */
@media (min-width: 992px) {
  ul#contact-links > li > a:hover {
    background-size: calc(800px + 5rem);
  }
}

/* X-Large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) {
  ul#contact-links > li > a:hover {
    background-size: 800px;
  }
}
</style>
