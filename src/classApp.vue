<script setup>
import { ref, reactive } from 'vue';

class Bird {
    constructor(name) {
        this.name = name
        this.energy = 0
        this.visitedCities = []
        this.homeCity = 'Aarhus'
    }

    eatFood(grams) {
        this.energy += grams * 4
    }

    flyKilometers(kilometers) {
        this.energy -= kilometers * 2 + 10
    }

    flyToSpecificCity(cityObject) {
        this.flyKilometers(cityObject.distanceFromAarhus)
        this.visitedCities.push(cityObject.name)
    }
}

class City {
    constructor(name, distanceKms) {
        this.name = name
        this.distanceFromAarhus = distanceKms
    }
}

const pepita = reactive(new Bird("Pepita"))
const paris = new City('Paris', 4) 

const gramsToEat = ref(0);
const kmsToFly = ref(0);

</script>


<template>
 <img
    src="https://chirpforbirds.com/wp-content/uploads/2021/02/Blog-featured-image-2-Kingfisher.jpg"
    alt="Kingfisher"
    width="400"
  />

  <h1> {{ pepita.name }}'s' energy: {{ pepita.energy }}</h1>

  <input type="number" v-model="gramsToEat" placeholder="Grams" />
  <button @click="pepita.eatFood(gramsToEat)">Eat</button>

  <input type="number" v-model="kmsToFly" placeholder="Kilometers" />
  <button @click="pepita.flyKilometers(kmsToFly)">Fly</button>

  <h2>Cities to Visit</h2>
  <button @click="pepita.flyToSpecificCity(paris)" :disabled="pepita.energy <= 0">Go to Paris</button>

  <h2>Visited Cities</h2>
  <ul>
    <li v-for="city in pepita.visitedCities">
      {{ city }}
    </li>
  </ul>
</template>

<style scoped>
img {
  border: 3px solid black;
}

</style>
