<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
    <div style="text-align: center;">
        <img alt="Turtle logo" class="logo" src="https://12ax7web.s3.amazonaws.com/accounts/1/storefronts/1/tt-logo-main.svg" width="300" height="300" />
    <div>
      
      <nav v-if="$route.name != 'tee_shirts'" style="text-align: center;">
        <RouterLink to="/tee_shirts/0">Voir la liste des tee-shirts</RouterLink>
      </nav>
    </div>
    </div>
    <RouterView />
</template>

<style>
@import '@/assets/base.css';

body {
  background-color: #f7f7f7;
}

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
