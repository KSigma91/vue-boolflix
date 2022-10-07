<template>
  <div id="app">
    <header>
      <NavbarHeader @myButton="receivedText"/>
    </header>

    <MainContent
      :search="userInput"
      :moviesResults="movieList"
      :seriesResults="seriesList"
    />
  </div>
</template>

<script>
import axios from 'axios'
import NavbarHeader from "./components/NavbarHeader.vue"
import MainContent from "./components/MainContent.vue"

export default {
  name: 'App',
  components: {
    NavbarHeader,
    MainContent
  },
  data() {
    return {
      // inputText: "",
      apiUrl: 'https://api.themoviedb.org/3/search/',
      myKey: '95ab071c54b74df27fd2f8b34c0fb2ab',
      movieList: [],
      seriesList: [],
      generalList: [],
      userInput: false
    }
  },
  created() {
    //this.getElement();
  },
  methods: {
    getMovies(apiParams) {
        axios
          .get(this.apiUrl + 'movie', apiParams)
          .then((element) => {
          this.movieList = element.data.results;
          this.generalList = [...this.movieList, ...this.seriesList];
          this.userInput = true;
          console.log(element);
        })
        .catch((error) => {
          console.log("Errore", error);
        })
    },
    getSeries(apiParams) {
      axios
        .get(this.apiUrl + 'tv', apiParams)
        .then((element) => {
          this.seriesList = element.data.results;
          this.generalList = [...this.movieList, ...this.seriesList];
          this.userInput = true;
          console.log(element);
        })
        .catch((error) => {
          console.log("Errore", error);
        })
    },
    // getList(list) {
    //     this.userInput = list;
    // },
    receivedText(searchText) {
      // this.userInput = searchText;
      // console.log(searchText);
      //this.getElement();
      const paramsObject = {
        params: {
          api_key: this.myKey,
          query: searchText,
          language: 'it-IT'
        }
      };
      this.getMovies(paramsObject);
      this.getSeries(paramsObject);
    }
  },
  computed: {
    getResults() {
      return [...this.movieList, ...this.seriesList];
    }
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0 !important;
  padding: 0;
}

body {
  min-height: 100vh;
  background: #434343; 
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
