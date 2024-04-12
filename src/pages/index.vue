<script setup lang="ts">
import { ref } from 'vue'
const sectionOpen = ref(1)
const sectionOpenData = ref()

const carrouselActif = ref(0)

const sectionsData = [
  {
    label: 'bouton 1',
    texte: `texte panneau 1 Lorem ipsum dolor sit ame
    consectetur adipisicing elit. Inventore animi dolore,
    rerum magni laudantium quod excepturi laboriosam, 
    ex modi debitis harum reprehenderit eaque quam ut
    ea molestiae. Id, cum dolor!`
  },
  {
    label: 'bouton 2',
    texte: `texte panneau 2 Amet alias provident quos quis, 
    Officia ut ab dolores quos dolorem accusamus ad,
    consectetur unde minima, ipsum eligendi inventore id
    labore, laborum rerum laboriosam corrupti iste.
    Distinctio, perspiciatis!`
  },
  {
    label: 'bouton 3',
    texte: `texte panneau 3 Repudiandae corporis voluptates, 
    odit reprehenderit sint pariatur at voluptatum, cumque
    quia sit eligendi ex culpa eos, alias magnam molestiae
    id modi accusantium ipsa eveniet accusamus. Tempora 
    quis corporis et nam.`
  }
]
</script>

<template>
  <h1 class="text-2xl">Bonjour monde !</h1>
  <section>
    <button class="text-xl" @pointerdown="sectionOpen = 1">bouton 1</button>
    <p v-show="sectionOpen === 1">
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Qui, explicabo placeat. Nisi officia
      dolorum dolor quas aliquid. Veniam quidem odio quisquam tempora dolorum illum vel quas?
      Molestias ipsa facere et?
    </p>
  </section>
  <section>
    <button class="text-xl" @pointerdown="sectionOpen = 2">bouton 2</button>
    <p v-show="sectionOpen === 2">
      Voluptate adipisci vitae distinctio autem omnis, deserunt rem optio dolor dicta fugiat sit non
      veritatis eum molestias odit, nulla magnam exercitationem? Exercitationem ratione quia nihil.
      Molestiae provident rerum esse ratione?
    </p>
  </section>
  <section>
    <button class="text-xl" @pointerdown="sectionOpen = 3">bouton 3</button>
    <p v-show="sectionOpen === 3">
      Saepe assumenda praesentium suscipit incidunt vel veritatis ad tempore, ut sapiente itaque
      rerum sit voluptatem eveniet aliquid delectus quae velit a error quia. Quaerat unde voluptatum
      sint doloremque eos officiis?
    </p>
  </section>
  <section v-for="({ label, texte }, key) of sectionsData" :key="key">
    <button class="text-xl" @pointerdown="sectionOpenData = sectionOpenData === (key+1) ? null : (key+1)">
      {{ label }} (data json)
    </button>
    <section v-show="sectionOpenData === (key+1)">
      <pre class="font-mono">key : {{ key }}</pre>
      <pre class="font-mono">label : {{ label }}</pre>
      <pre class="font-mono">texte : {{ texte }}</pre>
    </section>
  </section>
  <div class="relative">
    <button
      class="grid place-content-center absolute top-2/4 left-0 bg-black/50 rounded-full text-white p-8 w-8 cursor-pointer"
      aria-label="slide précedent"
      @pointerdown="carrouselActif = carrouselActif === 0 ? 0 : carrouselActif - 1"
    >
      <
    </button>
    <button
      class="grid place-content-center absolute top-2/4 right-0 bg-black/50 rounded-full text-white p-8 w-8 cursor-pointer"
      aria-label="slide suivant"
      @pointerdown="carrouselActif = carrouselActif === 4 ? 4 : carrouselActif + 1"
    >
      >
    </button>
    <div
      class="flex w-full overflow-x-scroll overflow-hidden rounded-lg snap-mandatory snap-x scroll-smooth"
      x-ref="parent"
      @scroll=""    >
      <div id="ecran-1" class="flex-none w-full text-center snap-start">
        <figure class="m-0">
          <img
            class="h-auto w-max"
            src="https://picsum.photos/seed/1/500/300"
            alt="image ecran 1"
          />
          <figcaption>Écran 1</figcaption>
        </figure>
      </div>
      <div id="ecran-2" class="flex-none w-full text-center snap-start">
        <figure class="m-0">
          <img
            class="h-auto w-max"
            src="https://picsum.photos/seed/2/500/300"
            alt="image ecran 2"
          />
          <figcaption>Écran 2</figcaption>
        </figure>
      </div>
      <div id="ecran-3" class="flex-none w-full text-center snap-start">
        <figure class="m-0">
          <img
            class="h-auto w-max"
            src="https://picsum.photos/seed/3/500/300"
            alt="image ecran 3"
          />
          <figcaption>Écran 3</figcaption>
        </figure>
      </div>
      <div id="ecran-4" class="flex-none w-full text-center snap-start">
        <figure class="m-0">
          <img
            class="h-auto w-max"
            src="https://picsum.photos/seed/4/500/300"
            alt="image ecran 4"
          />
          <figcaption>Écran 4</figcaption>
        </figure>
      </div>
      <div id="ecran-5" class="flex-none w-full text-center snap-start">
        <figure class="m-0">
          <img
            class="h-auto w-max"
            src="https://picsum.photos/seed/5/500/300"
            alt="image ecran 5"
          />
          <figcaption>Écran 5</figcaption>
        </figure>
      </div>
    </div>
    <ul class="flex justify-center gap-4">
      <li>
        <a
          href="#ecran-1"
          class="bg-gray-300 rounded-md p-2 flex mt-3 hover:bg-yellow-500 transition-all"
          >Écran 1</a
        >
      </li>
      <li>
        <a
          href="#ecran-2"
          class="bg-gray-300 rounded-md p-2 flex mt-3 hover:bg-yellow-500 transition-all"
          >Écran 2</a
        >
      </li>
      <li>
        <a
          href="#ecran-3"
          class="bg-gray-300 rounded-md p-2 flex mt-3 hover:bg-yellow-500 transition-all"
          >Écran 3</a
        >
      </li>
      <li>
        <a
          href="#ecran-4"
          class="bg-gray-300 rounded-md p-2 flex mt-3 hover:bg-yellow-500 transition-all"
          >Écran 4</a
        >
      </li>
      <li>
        <a
          href="#ecran-5"
          class="bg-gray-300 rounded-md p-2 flex mt-3 hover:bg-yellow-500 transition-all"
          >Écran 5</a
        >
      </li>
    </ul>
  </div>
</template>
