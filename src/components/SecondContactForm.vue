<script setup lang="ts">
import CallBackForm from './CallBackForm.vue';
</script>

<template>
    <section id="second_contact_form">
        <div class="container second_contact_form_wrap">
            <div class="left">
                <h2 class="small_title">заказ</h2>
                <h3 class="big_title">Хочу заказать!</h3>
                <p>Заполните форму и я свяжусь с вами в течении дня, для уточнения деталей заказа</p>
                <CallBackForm />
            </div>
            <img src="/public/images/cakes_contact.jpg" alt="Капкейки" class="right_img">
        </div>
    </section>
</template>

<style scoped lang="sass">
.second_contact_form_wrap 
    display: flex

    .left
        width: 50%
</style>