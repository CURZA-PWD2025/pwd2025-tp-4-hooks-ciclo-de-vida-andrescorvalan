<template>
   <div>
      <h1>Listado de tareas</h1>

      <p>Para agregar la nueva tares presione enter o clic en:</p>
      <input class="in_tarea" type="text" v-model="new_tarea" @keyup.enter="agregar">      
      <button class="bot_agregar" @click="agregar">Agregar tarea</button>

      <p v-if="lista_tareas.length">Tareas ya cargadas
         <ol>
            <li v-for="(tarea, index) in lista_tareas" :key="index" :ref="etiq => etiquetas[index]=(etiq as HTMLElement)">
               <!-- Lo que me costo ese "as HTMLElement"!!!!!!!!, si eso me marcaba error, aunq andaba -->
               {{tarea}}
            </li>
         </ol>
      </p>
      <p v-else>Ninguna tarea cargada</p>
   </div>
</template>


<script setup lang="ts">
   import { onBeforeUpdate,onUpdated } from 'vue'
   import { ref } from 'vue' 
  
   const new_tarea = ref('')
   const lista_tareas = ref<string[]>([])
   const etiquetas = ref<(HTMLElement | null)[]>([])

   function agregar(){
      if(new_tarea.value)
         lista_tareas.value.push(new_tarea.value)
      new_tarea.value=''
   }

   onBeforeUpdate(()=>{
      console.log(' **"Lista aún no modificada"**')
      etiquetas.value.forEach(una_etiq => {
         if(una_etiq)
            una_etiq.style.color='red'
      });
   })
   onUpdated(()=>{
      console.log('**"Lista modificada"**')
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
   ol{
      text-align: left;
      color: green;
   }
   .in_tarea,.bot_agregar{
      display: inline-block;
      margin: 0 0.5em;
   }
   p {
      text-align: left;
      color: blue;
   }
</style>