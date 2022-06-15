<template>
   <div class="card">
        <h3>{{ insertCard.title }}</h3>
        <h3>{{ insertCard.original_title }}</h3>
        <h3>{{ insertCard.original_language }}</h3>
        <h3>{{ insertCard.vote_average }}</h3>
   </div>
</template>

<script>
export default {
    name: "MyCard",
    props: {
        insertCard: Object
    }
}
</script>

<style scoped lang="scss">
</style>