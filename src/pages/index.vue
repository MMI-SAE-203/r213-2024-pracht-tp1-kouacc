<script setup lang="ts">
import { ref } from 'vue'
const sectionOpen = ref(1)
</script>

<template>
  <h1 class="text-2xl">Bonjour monde !</h1>
  <section>
    <button class="text-xl" @pointerdown="sectionOpen = 1">bouton 1</button>
    <p v-show="sectionOpen === 1">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Qui, explicabo placeat. Nisi
      officia dolorum
      dolor quas
      aliquid. Veniam quidem odio quisquam tempora dolorum illum vel quas? Molestias ipsa facere et?</p>
  </section>
  <section>
    <button class="text-xl" @pointerdown="sectionOpen = 2">bouton 2</button>
    <p v-show="sectionOpen === 2">Voluptate adipisci vitae distinctio autem omnis, deserunt rem optio dolor dicta fugiat
      sit non
      veritatis eum
      molestias odit, nulla magnam exercitationem? Exercitationem ratione quia nihil. Molestiae provident rerum esse
      ratione?</p>
  </section>
  <section>
    <button class="text-xl" @pointerdown="sectionOpen = 3">bouton 3</button>
    <p v-show="sectionOpen === 3">Saepe assumenda praesentium suscipit incidunt vel veritatis ad tempore, ut sapiente
      itaque rerum sit
      voluptatem
      eveniet aliquid delectus quae velit a error quia. Quaerat unde voluptatum sint doloremque eos officiis?</p>
  </section>
</template>
