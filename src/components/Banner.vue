<template>
    <div id="main-banner"></div>
</template>

<script>
    export default{
       name: "Banner", 
    }
</script>

<style scoped>
    #main-banner{
        background-image: linear-gradient(rgba(0,0,0,0.5),rgba(0,0,0,0.5)), url('/img/burguer.jpg');
        background-position: bottom;
        background-size: cover;
        height: 580px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }
</style>
