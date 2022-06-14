<template>
    <div class="container">
        <h2>{{ card.title }}</h2>
        <h2>{{ card.original_title }}</h2>
        <h2>{{ card.original_language }}</h2>
        <h2>{{ card.vote_average }}</h2>
    </div>
</template>

<script>
export default {
    name: 'MainContent',
    props: {
        title: String,
        originalTitle: String,
        card: Object
    },
}
</script>

<style scoped lang="scss">
.container {
    width: 100%;
    height: calc(100vh - 60px);
}
</style>