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
    <button
      aria-controls="mainNav"
      aria-expanded="true"
      class="rounded-full border-2 border-red-600 bg-red-300 px-2"
      @pointerdown="menuIsOpen = !menuIsOpen"
    >
      menu
    </button>
    <!-- nav#mainNav>ul>li*3>a[href="#"]{item $} -->
    <Transition
      class="transition-transform duration-1000"
      enter-from-class="-translate-x-full"
      enter-to-class="translate-x-0"
      leave-active-class="-translate-x-full"
    >
      <nav
        id="mainNav"
        v-show="menuIsOpen"
        class="bg-orange-600 mx-auto p-10 w-1/3 rounded-xl shadow-xl border border-gray-800"
      >
        <ul class="mx-auto flex flex-col gap-3">
          <li class="text-lg bg-orange-300 p-2 rounded-lg border border-black">
            <a href="#">item 1</a>
          </li>
          <li class="text-lg bg-orange-300 p-2 rounded-lg border border-black">
            <a href="#">item 2</a>
          </li>
          <li class="text-lg bg-orange-300 p-2 rounded-lg border border-black">
            <a href="#">item 3</a>
          </li>
        </ul>
      </nav>
    </Transition>
  </header>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
</template>
