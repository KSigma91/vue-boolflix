<template>
    <main>
        <section class="movies" v-if="moviesResults.length">
            <ul>
                <li>
                    <h2>Movies</h2>
                    <MyCard v-for="(movie, index) in moviesResults" :key="index"
                    :insertCard="movie"/>
                </li>  
            </ul>
        </section>
        <section class="series" v-if="seriesResults.length">
            <ul>
                <li>
                    <h2>Series</h2>
                    <MyCard v-for="(serie, index) in seriesResults" :key="index"
                    :insertCard="serie"/>
                </li>
            </ul>
        </section>
    </main>
</template>

<script>
import MyCard from './MyCard.vue'

export default {
    name: "MainContent",
    components: {
        MyCard
    },
    props: {
        search: Boolean,
        moviesResults: Array,
        seriesResults: Array
    }
}
</script>

<style lang="scss" scoped >
main {
    
    h2 {
        text-align: start;
        padding: 30px 80px;
        color: #ffffff;
    }

    li {
        list-style-type: none;
    }
}
</style>