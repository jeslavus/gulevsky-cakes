<script setup lang="ts">
import { ref, onMounted, markRaw } from 'vue';
import work_process from '@/json/work_process.json';

const svgComponents = ref<Record<string, any>>({});

onMounted(async () => {
    try {
        const imports: Promise<void>[] = work_process.list.map(async item => {
            const module = await import(`@/assets/svg/${item.svg}.vue`);
            svgComponents.value[item.svg] = markRaw(module.default);
        });
        await Promise.all(imports);
    } catch (error) {
        console.error('Error loading SVG components:', error);
    }
});
</script>

<template>
    <section id="work_process">
        <div class="container">
            <h2 class="small_title">{{ work_process.title }}</h2>
            <ul class="work_process_list reset_ul">
                <li class="work_process_item" v-for="item in work_process.list" :key="item.title">
                    <figure>
                        <component :is="svgComponents[item.svg]" />
                        <figcaption>
                            <h3>{{ item.title }}</h3>
                            <p>{{ item.text }}</p>
                        </figcaption>
                    </figure>
                </li>
            </ul>
        </div>
    </section>
</template>

<style scoped lang="sass">
.work_process_list
    display: flex
    gap: 20px

    .work_process_item
        width: 100%
        font-variant-numeric: lining-nums tabular-nums

        h3
            color: #C44536
            font-family: Prata
            font-size: 20px
            font-weight: 400

        p
            color: #32292F
            font-family: Gilroy
            line-height: 150%
</style>
