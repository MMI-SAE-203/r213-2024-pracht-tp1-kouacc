<script setup lang="ts">
import { onErrorCaptured, ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'

onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})

const menuIsOpen = ref(false)
</script>

<template>
  <header>
    <button aria-controls="mainNav" aria-expanded="true" class="rounded-full border-2 border-red-600 bg-red-300 px-2"
      @pointerdown="menuIsOpen = !menuIsOpen">
      menu
    </button>
    <!-- nav#mainNav>ul>li*3>a[href="#"]{item $} -->
    <nav id="mainNav" v-show="menuIsOpen">
      <ul>
        <li><a href="#">item 1</a></li>
        <li><a href="#">item 2</a></li>
        <li><a href="#">item 3</a></li>
      </ul>
    </nav>
  </header>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
</template>
