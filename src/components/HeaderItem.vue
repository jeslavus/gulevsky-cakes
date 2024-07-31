<script setup lang="ts">
import { RouterLink, useRoute } from 'vue-router';
import headerMenu from '../json/header_menu.json';
import contacts from '../json/contacts.json';
import LogoSVG from '@/assets/svg/LogoSVG.vue';
import Telegram from '@/assets/svg/Telegram.vue';
import { computed } from 'vue';
import PhoneIcon from '@/assets/svg/PhoneIcon.vue';

// Получение текущего маршрута
const route = useRoute();
const isHomePage = computed((): boolean => route.path === '/');
</script>

<template>
  <header>
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
          <li v-for="item in headerMenu" :key="item.link" class="header_menu_item">
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
        <ul class="contacts_menu reset_ul">
          <li v-for="item in contacts" :key="item.link" class="contacts_menu_item">
            <a v-if="item.type === 'phone'" :href="item.link">
              <PhoneIcon />
              <span>{{ item.view }}</span>
            </a>
            <a v-else :href="item.link">
              <Telegram />
            </a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<style scoped></style>
