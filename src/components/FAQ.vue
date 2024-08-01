<script setup lang="ts">
import Plus from '@/assets/svg/Plus.vue';
import faq from '@/json/faq.json';
</script>

<template>
    <section id="faq">
        <div class="container">
            <h2 class="small_title">{{ faq.title }}</h2>
            <h3 class="big_title">{{ faq.subtitle }}</h3>
            <ul class="faq_list reset_ul">
                <li class="faq_list_item" v-for="item in faq.list" :key="item.question">
                    <details>
                        <summary class="question">
                            <h4>{{ item.question }}</h4>
                            <Plus />
                        </summary>
                        <div class="answer">{{ item.answer }}</div>
                    </details>
                </li>
            </ul>
        </div>
    </section>
</template>

<style scoped lang="sass">
.small_title,
.big_title
    text-align: center

.faq_list_item
    border-bottom: 1px solid #DDCEC2
    padding-bottom: 16px
    margin-top: 24px

    details[open] 
        .vertical
            opacity: 0

    .question
        display: flex
        justify-content: space-between
        align-items: center
        gap: 20px

        h4
            color: #32292F
            font-variant-numeric: lining-nums tabular-nums
            font-family: Gilroy
            font-size: 24px
            font-weight: 400
            line-height: 150%
            margin: 0

    .answer
        padding-top: 16px
</style>