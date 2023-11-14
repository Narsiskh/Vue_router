<script setup>
import carsData from "../Data.json"
import {useRouter, useRoute} from "vue-router"
import {ref, watch, onMounted} from "vue"

const router = useRouter()
const route = useRoute()

const cars = ref(carsData)
const make = ref("")

onMounted(() => {
  make.value = route.query.make
})

watch(make, () => {
  if(make.value){
    if(make.value === "All") cars.value = carsData;
    else {
      cars.value = carsData.filter(c => c["make"] === make.value)
    }
  }
})

const handleChange = () => {
  router.push({query: {make: make.value}})
}
</script>

<template>
  <div class="container">
    <h1>Our Cars</h1>
    <select @change="handleChange" v-model="make">
      <option value="All">All</option>
      <option value="Chevrolet">Chevy</option>
      <option value="Porsche">Porsche</option>
      <option value="Audi">Audi</option>
    </select>
    <div class="cards">
      <div
          v-for="car in cars"
          :key="car.id"
          class="card"
          @click="$router.push(`/car/${car.id}`)"
      >
        <h1>{{car['make']}}</h1>
        <p>${{car['price']}}</p>
      </div>
    </div>
  </div>
</template>

<style src="../assets/home.sass" scoped lang="sass"></style>