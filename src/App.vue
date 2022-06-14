<template>
  <div id="app">
    <header>
      <NavbarHeader/>
    </header>

    <main>
      <MainContent/>
    </main>
  </div>
</template>

<script>
import NavbarHeader from "./components/NavbarHeader.vue"
import MainContent from "./components/MainContent.vue"

export default {
  name: 'App',
  components: {
    NavbarHeader,
    MainContent
}
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0 !important;
  padding: 0;
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
