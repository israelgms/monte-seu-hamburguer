<template>
  <div class="main-container">
    <Dashboard />
  </div>
  <div class="espacamento"></div>
</template>

<script>
import Dashboard from "../components/Dashboard.vue"

export default {
  name: "Pedidos",
  components: {
    Dashboard,
  }
}
</script>

<style scoped>
  .espacamento{
    margin-top: 420px;
  }
</style>