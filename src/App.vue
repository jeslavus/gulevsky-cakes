<script setup lang="ts">
import Header from './components/HeaderItem.vue';
import Footer from './components/FooterItem.vue';
import { RouterView, useRoute } from 'vue-router';
import { computed } from 'vue';

// Получение текущего маршрута
const route = useRoute();
const isNotFoundPage = computed((): boolean => route.name === 'NotFound');
</script>

<template>
  <Header v-if="!isNotFoundPage" />
  <main>
    <RouterView />
  </main>
  <Footer v-if="!isNotFoundPage" />
</template>

<style scoped></style>