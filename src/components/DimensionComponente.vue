<template>
   <div>
      <h1>Dimension del componente</h1>
      <p>Coordenadas inner</p>
      <p>Coordenada X: {{inner_x}}</p>
      <p>Coordenada Y: {{inner_y}}</p>
      <p>Coordenadas outer</p>
      <p>Coordenada X: {{outer_x}}</p>
      <p>Coordenada Y: {{outer_y}}</p>
   </div>
</template>

<script setup lang="ts">
   import { onMounted, onUnmounted } from 'vue';
   import { ref } from 'vue' 
  
   const inner_x = ref(window.innerWidth)
   const inner_y = ref(window.innerHeight)
   const outer_x = ref(window.outerWidth)
   const outer_y = ref(window.outerHeight)

   function escuchar_resize(){
      inner_x.value=window.innerWidth
      inner_y.value=window.innerHeight
      outer_x.value=window.outerWidth
      outer_y.value=window.outerHeight
   }
   onMounted(()=>{
      window.addEventListener('resize', escuchar_resize)
   })
   onUnmounted(()=>{
      window.removeEventListener('resize', escuchar_resize)
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
</style>


