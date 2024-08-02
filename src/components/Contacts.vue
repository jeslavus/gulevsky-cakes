<script setup lang="ts">
import PhoneIcon from '@/assets/svg/PhoneIcon.vue';
import Pin from '@/assets/svg/Pin.vue'
import Telegram from '@/assets/svg/Telegram.vue';
import VK from '@/assets/svg/VK.vue';
import WhatsApp from '@/assets/svg/WhatsApp.vue';
</script>

<template>
    <section id="contacts">
        <div class="container">
            <h2 class="big_title">Мои контакты</h2>
            <address>
                <Pin />
                <span>г. Липецк, ул. Неделина, д. 16</span>
            </address>
            <a href="#">
                <PhoneIcon />
                <span>+7 (904) 282-85-33</span>
            </a>
            <ul class="social_links_list reset_ul">
                <li class="social_links_list_item">
                    <a href="#">
                        <VK />
                    </a>
                </li>
                <li class="social_links_list_item">
                    <a href="#">
                        <Telegram />
                    </a>
                </li>
                <li class="social_links_list_item">
                    <a href="#">
                        <WhatsApp />
                    </a>
                </li>
            </ul>
        </div>
    </section>
</template>

<style scoped lang="sass">
#contacts
    .container
        display: flex
        flex-direction: column
        justify-content: center
        align-items: center
        gap: 10px

        .social_links_list
            display: flex
            align-items: center
            justify-content: center
            gap: 8px
</style>