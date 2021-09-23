<template>
  <Navbar :logo="logo_src" :alt="alt_name" />
  <router-view/>
  <Footer />
</template>

<script>
import Navbar from "./components/Navbar.vue"; 
import Footer from "./components/Footer.vue";

export default{
  components:{
    Navbar,
    Footer
  },
  data(){
    return{
      logo_src: "/img/logo.png",
      alt: "Monte seu Hamburguer"
    }
  }
}
</script>

<style>

  * {
    font-family: Arial, Helvetica, sans-serif;
    padding: 0;
    border: none;
    margin: 0;
    list-style: none;
    box-sizing: border-box;
    --pretoPrincipal: #242424;
    --preto: rgb(24, 24, 24);
    --amarelo: #FCBA03;
  }

  .main-container{
    margin: 50px;
    min-height: 250px;
  }

  h1{
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color: var(--pretoPrincipal);
  }

</style>
