<template>
    <header>
        <div v-for="(element, index) in filteredSearch"
        :key="index" :title="element.title" :originalTitle="element.original_title" :card="element.results"></div>
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
            apiUrl: "https://api.themoviedb.org/3/search/top_rated?api_key=95ab071c54b74df27fd2f8b34c0fb2ab",
            listArray: [],
            userText: ""
        }
    },
    created() {
        this.listArray = this.apiUrl;
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
                return this.listArray.filter(item => {
                    return item.results.toLowerCase().includes(this.userText.toLowerCase());
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