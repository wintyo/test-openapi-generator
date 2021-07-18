<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 + TypeScript + Vite" />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import { PetsApi } from '../api-generator/client/'

const api = new PetsApi({
  basePath: 'http://localhost:3001/v1'
})

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld
  },
  setup: () => {
    console.log(api)

    api.listPets()
      .then((result) => {
        console.log(result)
      })

    return {}
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
