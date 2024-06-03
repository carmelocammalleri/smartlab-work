<script>
  import Header from "./components/Header.vue";
  import Footer from "./components/Footer.vue";
  import Main from "./components/Main.vue";
  
  export default {
    name: 'App',
    components:{
      Header,
      Footer,
      Main
    }
  }
</script>

<template>
  <div class="container-tot">
    <Header/>
    <Main />
    <Footer/>
  </div>
</template>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

</style>
