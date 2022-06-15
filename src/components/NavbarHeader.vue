<template>
    <header>
        <div v-for="(element, index) in listArray"
        :key="index" :myTitle="element.title" :originalTitle="element.original_title" :originalLanguage="element.original_language" :voteAverage="element.vote_average" :card="element"
        @inputSearch="getContent"></div>
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
            apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=95ab071c54b74df27fd2f8b34c0fb2ab&query=Django+Unchained",
            listArray: [],
            userText: ""
        }
    },
    created() {
        this.getContent();
    },
    methods: {
        getContent() {
            axios.get(this.apiUrl).then((result) => {
                this.listArray = result.data.results;
                console.log(result);
            })
            .catch((error) => {
                console.log("Errore", error);
            })
        },
        getResult(list) {
            this.userText = list;
            console.log(list);
        }
    },
    computed: {
        filteredSearch() {
            if(this.userText === "") {
                return this.listArray;
            } else {
                return this.listArray.filter(listElement => {
                    return listElement.toLowerCase().includes(this.userText.toLowerCase());
                });
            }
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