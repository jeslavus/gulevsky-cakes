<template>
    <div class="not-found">
        <h1>404</h1>
        <p>Упс, такой страницы не существует.</p>
        <router-link to="/">Вернуться на главную</router-link>
    </div>
</template>

<script>
export default {
    name: 'NotFound'
}
</script>

<style scoped>
.not-found {
    text-align: center;
    margin-top: 50px;
}

.not-found h1 {
    font-size: 2rem;
    margin-bottom: 20px;
}

.not-found p {
    margin-bottom: 20px;
}
</style>