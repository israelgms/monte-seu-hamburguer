<template>
  <div id="nav">
    <router-link to="/" id="logo-url">
      <img :src="logo" :alt="alt" id="logo">
    </router-link>
    <router-link to="/">Inicio</router-link>
    <router-link to="/Pedidos">Pedidos</router-link>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  props: ["logo", "alt"]
};
</script>

<style scoped>
  #nav {
    background-color: var(--pretoPrincipal);
    padding: 15px 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }

  #nav #logo-url {
    margin: auto;
    margin-left: 0;
  }

  #logo {
    width: 50px;
    height: 50px;
  }

  #nav a {
    color: var(--amarelo);
    text-decoration: none;
    margin: 12px;
    transition: .5s;
    font-size: 21px;
  }

  #nav a:hover {
    color: #fff;
  }

</style>