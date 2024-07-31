<script setup lang="ts">
import { RouterLink, useRoute } from 'vue-router';
import footerMenu from '../json/footer_menu.json';
import LogoSVG from '@/assets/svg/LogoSVG.vue';
import { computed } from 'vue';

// Получение текущего маршрута
const route = useRoute();
const isHomePage = computed((): boolean => route.path === '/');
</script>

<template>
    <footer>
        <div class="container">
            <nav class="classic_nav">
                <template v-if="!isHomePage">
                    <router-link to='/'>
                        <LogoSVG />
                    </router-link>
                </template>
                <template v-else>
                    <LogoSVG />
                </template>
                <ul class="classic_fix_menu reset_ul">
                    <li v-for="item in footerMenu" :key="item.link" class="header_menu_item">
                        <!-- Проверка на соответствие текущему маршруту -->
                        <template v-if="route.path === item.link">
                            <p>{{ item.title }}</p>
                        </template>
                        <template v-else-if="item.link.startsWith('#')">
                            <a :href="item.link">{{ item.title }}</a>
                        </template>
                        <template v-else>
                            <router-link :to="item.link">{{ item.title }}</router-link>
                        </template>
                    </li>
                </ul>
            </nav>
        </div>
    </footer>
</template>

<style scoped></style>
