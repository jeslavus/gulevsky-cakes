<script setup lang="ts">
import NavigationMenu from '@/components/NavigationMenu.vue';
</script>

<template>
    <footer>
        <div class="container">
            <NavigationMenu />
            <nav class="footer_bottom">
                <router-link to="/policy/">Политика конфидециальности</router-link>
            </nav>
        </div>
    </footer>
</template>

<style scoped></style>
