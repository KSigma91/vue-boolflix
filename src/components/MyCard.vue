<template>
   <div class="card">
        <h3>{{ insertCard.title }}</h3>
        <h3>{{ insertCard.original_title }}</h3>
        <h3>{{ insertCard.original_language }}</h3>
        <h3>{{ insertCard.vote_average }}</h3>
        <img :src="getFlags" alt="flag_en_img">
   </div>
</template>

<script>
export default {
    name: "MyCard",
    props: {
        insertCard: Object
    },
    methods: {
        getFlags(flag) {
            this.listArray.original_language = flag;
        }
    }
}
</script>

<style scoped lang="scss">
.card {

    img {
        max-width: 100%;
        height: 50px;
    }
}
</style>