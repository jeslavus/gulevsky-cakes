<script setup lang="ts">
import { RouterLink, useRoute } from 'vue-router';
import headerMenu from '../json/header_menu.json';
import contacts from '../json/contacts.json';
import LogoSVG from '@/assets/svg/LogoSVG.vue';
import Telegram from '@/assets/svg/Telegram.vue';
import { computed } from 'vue';
import PhoneIcon from '@/assets/svg/PhoneIcon.vue';
import WhatsApp from '@/assets/svg/WhatsApp.vue';
import VK from '@/assets/svg/VK.vue';

// Получение текущего маршрута
const route = useRoute();
const isHomePage = computed((): boolean => route.path === '/');
</script>

<template>
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
            <li v-for="item in headerMenu" :key="item.link" class="header_menu_item">
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
        <ul class="contacts_menu reset_ul">
            <li v-for="item in contacts" :key="item.link" class="contacts_menu_item">
                <a v-if="item.type === 'phone'" :href="item.link" target="_blank">
                    <PhoneIcon />
                    <span>{{ item.view }}</span>
                </a>
                <a v-else :href="item.link" target="_blank">
                    <Telegram v-if="item.type === 'telegram'" />
                    <WhatsApp v-else-if="item.type === 'whatsapp'" />
                    <VK v-else-if="item.type === 'VK'" />
                </a>
            </li>
        </ul>
    </nav>
</template>