<script setup>
import carsData from "../Data.json";
import {ref} from "vue";

const cars = ref(carsData);
</script>

<template>
  <main class="container">
    <h1>Our Cars</h1>
    <div class="cards">
      <div v-for="car in cars" :key="car.id" class="card">
        <h1>{{car['make']}}</h1>
        <p>${{car['price']}}</p>
      </div>
    </div>
  </main>
</template>

<style src="../assets/home.sass" scoped lang="sass"></style>