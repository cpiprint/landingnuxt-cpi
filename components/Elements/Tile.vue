<template>
  <div @click="goToComponentIndex(props.data.name)"
    class="col-span-full h-auto transform-gpu cursor-pointer rounded-lg bg-dark-200/50 p-1 transition-transform duration-300 ease-in-out will-change-transform hover:rotate-2 odd:hover:-rotate-2 sm:col-span-6 md:col-span-4 2xl:col-span-3 dark:bg-dark-500/10">
    <div class="flex h-56 w-full items-center justify-center rounded-md bg-dark-200/60 dark:bg-dark-500/10">
      <LazyElementsHeroCover v-if="props.data.name === 'hero'" />
      <LazyElementsHeadersCover v-if="props.data.name === 'headers'" />
      <LazyElementsFeaturesCover v-if="props.data.name === 'features'" />
      <LazyElementsFootersCover v-if="props.data.name === 'footers'" />
    </div>
    <div class="mt-2 p-1 text-base font-bold capitalize text-dark-950/90 dark:text-dark-50/90">
      {{ props.data.name }}
      <small class="text-dark-400 dark:text-dark-500">({{
        props.data.total === 0
          ? "Cooming soon"
          : `${props.data.total}
        components`
      }})</small>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { Component } from "~/types/index";

const props = defineProps<{
  data: Component;
}>();

function goToComponentIndex(name: string) {
  navigateTo(`/components/${name}`);
}
</script>
