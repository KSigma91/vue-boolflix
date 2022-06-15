<template>
    <div class="container">
        <MyCard v-for="(item, index) in listArray" :key="index"
        :insertCard="item"/>
    </div>
</template>

<script>
import axios from 'axios';
import MyCard from './MyCard.vue'


export default {
    name: "MainContent",
    components: {
       MyCard
    },
    props: {
        msg: String
    },
    data() {
        return {
            apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=95ab071c54b74df27fd2f8b34c0fb2ab&query=Django+Unchained",
            listArray: [],
            userInput: ""
        };
    },
    created() {
        this.getElement()
    },
    methods: {
        getElement() {
            axios.get(this.apiUrl).then((element) => {
                this.listArray = element.data.results;
                console.log(element);
            })
            .catch((error) => {
                console.log("Errore", error);
            })
        } ,
        getList(list) {
            this.userInput = list;
        }
    }
}
</script>

<style scoped lang="scss">
.container {
    width: 100%;
    height: calc(100vh - 60px);
}
</style>