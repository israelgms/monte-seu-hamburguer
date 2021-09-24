<template>
    <form @submit="cadastrar">
        <label>Nome</label>
        <input type="text" v-model="nome">
        <label>Email</label>
        <input type="text" v-model="email">
        <label>Telefone</label>
        <input type="text" v-model="telefone">
        <label>Endereço</label>
        <input type="text" v-model="endereço">
        <input type="submit">
    </form>
</template>

<script>

export default {
    name: "CadastroForm",
    data(){
        return{
            nome: "",
            email: "",
            telefone: "",
            endereco: ""
        }
    },
    methods:{ 
        async cadastrar(e){
            e.preventDefault();            
        }
    }
}


</script>