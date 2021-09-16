<template>
<footer id="footer">
    <p>Israel Gomes. Monte seu Hamburguer &copy; 2021</p>
</footer>
</template>

<script>
export default {
    name: "Footer"
}
</script>

<style scoped>
    #footer{
        height: 100px;
        background-color: var(--pretoPrincipal);
        border-top: 4px solid var(--preto);
        color: var(--amarelo);
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
    }
</style>