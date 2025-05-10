<template>
   <div>
      <h1>Listado de profesiones</h1>
      <ul v-if="lista_profesiones.length">
         <li v-for="(profesion, index) in lista_profesiones" :key="index">
            <p>{{profesion.nombre}}: {{profesion.descripcion}}</p>
         </li>
      </ul>
      <p v-else>Cargando...</p>
   </div>
</template>

<script setup lang="ts">
   import { onMounted } from "vue";
   import { ref } from "vue";
   import { profesiones }  from "../../resource/profesiones"
   import type { Profesion } from "../../resource/interfaces/profesion";

   const lista_profesiones=ref<Profesion[]>([])

   onMounted(()=>{
      setTimeout(() => {
         lista_profesiones.value = profesiones
      }, 3000)
   })
</script>

<style scoped>
   h1 {
      font-size: 1.5em;
      font-family: Georgia, 'Times New Roman', Times, serif;
   }
   div {
      border: 1px solid blue;
      border-radius: 10px;
      padding: 0.5em;
      margin:0.5em;
   }
   ul {
      list-style: none;
      text-align: left;
   }
</style>