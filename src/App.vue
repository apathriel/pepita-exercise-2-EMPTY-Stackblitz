<template>
  <!-- Her er vores dom elementer -->

  <!--indsat billede fra nettet-->
  <img
    src="https://chirpforbirds.com/wp-content/uploads/2021/02/Blog-featured-image-2-Kingfisher.jpg"
    alt="Kingfisher"
    width="400"
  />

  <h1>Pepita's energy: {{ pepita.energy }}</h1>

  <input type="number" v-model="gramsToEat" placeholder="Grams" />
  <button @click="eat">Eat</button>

  <input type="number" v-model="kmsToFly" placeholder="Kilometers" />
  <button @click="fly">Fly</button>
</template>
<script>
import { ref } from 'vue';
export default {
  setup() {
    const test = ref(true);

    function testFunc(event) {}

    return {
      test,
      testFunc,
    };
  },
};
</script>
