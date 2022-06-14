<template>
    <header>
        <SearchFunction @inputSearch="getResult"/>
    </header>
</template>

<script>
import axios from 'axios'
import SearchFunction from './SearchFunction'

export default {
    name: 'NavbarHeader',
    components: {
        SearchFunction
    }, 
    data() {
        return {
            apiUrl: "https://api.themoviedb.org/3/movie/top_rated?api_key=95ab071c54b74df27fd2f8b34c0fb2ab",
            userSearch: ""
        }
    },
    methods: {
        getResult() {
            axios.get(this.apiUrl).then((result) => {
                this.userSearch = result.data.results;
                console.log(result);
            })
            .catch((error) => {
                console.log("Errore", error);
            })
        }
    } 
}
</script>

<style scoped lang="scss">
    header {
        display: flex;
        justify-content: flex-end;
        align-items: center;
        padding-right: 20px;
        background: #000;
        width: 100%;
        height: 60px;
    }
</style>