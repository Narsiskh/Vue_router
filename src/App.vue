<script setup>
import {RouterView, RouterLink} from "vue-router"

</script>

<template>
  <main>
    <div class="links">
      <RouterLink active-class="active" to="/">Home</RouterLink>
      <RouterLink active-class="active" to="/about">About</RouterLink>
    </div>
    <RouterView />
  </main>
</template>

<style src="./assets/app.sass" scoped lang="sass"></style>
