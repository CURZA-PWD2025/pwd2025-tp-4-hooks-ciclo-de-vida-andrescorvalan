<script setup lang="ts">
   import Lista from "./components/Lista.vue"
   import Tareas from "./components/Tareas.vue"
   import DimensionComponente from "./components/DimensionComponente.vue"
   import { ref } from "vue";
   const componente = ref()
</script>

<template>
   <div class="principal">
      <nav>
         <button @click="componente = Lista" >Lista</button>
         <button @click="componente = Tareas" >Tareas</button>
         <button @click="componente = DimensionComponente" >DimensionComponente</button>
      </nav>
      <component :is="componente"/> 
   </div>
</template>

<style scoped>
   .principal {
      width: 100vw;
      min-height: 100vh;
    }
    nav {
      background-color: bisque;
    }
    button {
      background-color:steelblue;
      margin: 0.5em;
    }
</style>
