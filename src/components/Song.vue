<template>
  <div class="hover:bg-theme-300 rounded-4px overflow-hidden flex flex-col w-full">
    <div class="flex justify-between items-center">
      <div class="flex items-center gap-4">
        <div class="w-24 min-w-24">
          <Cover :cover="cover" />
        </div>
        <div class="flex flex-col w-auto md:w-64">
          <h1 class="text-lg">{{ song.is_remix ? song.title + " (Geoxor Remix)" : song.title }}</h1>
          <p class="text-theme-700">{{ song.artists.join(" & ") }}</p>
        </div>
        <p class="hidden md:flex text-theme-700 w-32">{{ song.date }}</p>
        <label
          class="hidden md:hidden lg:flex rounded-full border-2 select-none bg-opacity-0 hover:bg-opacity-10 bg-accent border-accent text-accent h-min px-2 py-0.5"
          >{{ song.type }}</label
        >
        <label
          v-if="song.is_remix"
          class="hidden md:hidden lg:flex rounded-full border-2 select-none bg-opacity-0 hover:bg-opacity-10 bg-[#0ff] border-[#0ff] text-[#0ff] h-min px-2 py-0.5"
          >Remix</label
        >
      </div>
      <div class="flex items-center gap-4 px-4">
        <a
          target="_blank"
          :href="song.link"
          class="rounded-full flex items-center gap-2 border-2 border-accent select-none bg-accent h-min text-white px-4 py-2"
          ><i-fluency-save /> Download</a
        >
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Song, Cover as ICover } from "~/interfaces";
import Cover from "./Cover.vue";
defineProps<{
  song: Song;
  cover?: ICover;
}>();
</script>
