<template>
  <Banner />
  <div class="main-container">
    <BurguerForm />
  </div>
</template>

<script>
  import Banner from "../components/Banner.vue"
  import BurguerForm from "../components/BurguerForm.vue"

  export default{
    name: "Inicio",
    components:{
      Banner,
      BurguerForm,
    }
  }


</script>
