<template>
    <div>
        <p>Componente Mensagem</p>
    </div>
    <div>
        <form id="burguer-form" @submit="createBurguer">
            <h1>Monte o seu burguer: </h1>
            <div class="input-container">
                <label for="nome">Nome do Cliente: </label>
                <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu Nome">
            </div>    
            <div class="input-container">
                <label for="pao">Escolha o pão</label>
                <select name="pao" id="pao" v-model="pao">
                    <option value="">Selecione o seu pão</option>
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{pao.tipo}}</option>
                </select>
            </div>    
            <div class="input-container">
                <label for="carne">Escolha a sua carne: </label>
                <select name="carne" id="carne" v-model="carne">
                    <option value="">Selecione o tipo de carne</option>
                    <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{carne.tipo}}</option>
                </select>
            </div>    
            <div id="opcionais-container" class="input-container">
                <label id="opcionais-title" for="opcionais">Selecione os opcionais: </label>
                <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id" >
                    <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                    <span>{{opcional.tipo}}</span>
                </div>
            </div>    
            <div class="input-container">
                <input type="submit" class="submit-btn" value="Montar Hamburguer">
            </div>
    
        </form>

    </div>
</template>

<script>
export default {
    name: "BurguerForm",
    data(){
        return{
            paes: null,
            carnes: null,
            opcionaisdata: null, // plural = dados que vem do servidor. Singular = enviados
            nome: null,
            pao: null,
            carne: null,
            opcionais: [],
            status: "Solicitado",
            msg: null,
        }        
    }, 
    methods: {
        //Pegando os dados do "Backend"
            async getIngredientes(){
                const req = await fetch("http://localhost:3000/ingredientes");
                const data = await req.json();

                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisdata = data.opcionais;
            },
            //Enviando os dados para o "Backend"
            async createBurguer(e){
                e.preventDefault();
                console.log("Criou o hamburguer")
            }
        },
        mounted(){ // quando o componente for montado, chamar a função getIngredientes
            this.getIngredientes()
        }
}
</script>

<style scoped>
    #burguer-form{
        max-width: 500px;
        margin: 0 auto;
    }
    .input-container{
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }
    label{
        font-weight: bold;
        margin-bottom: 15px;
        color: var(--pretoPrincipal);
        padding: 5px 10px;
        border-left: 4px solid var(--amarelo);
    }

    input, select {
        padding: 5px 10px;
        width: 500px;
    }

    #opcionais-container{
        flex-direction: row;
        flex-wrap: wrap;
    }

    #opcionais-title {
        width: 100%;
    }

    .checkbox-container{
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }

    .checkbox-container span,
    .checkbox-container input{
        width: auto;
    }

    .checkbox-container span{
        margin-left: 6px;
        font-weight: bold;
    }

    .submit-btn{
        background-color: var(--pretoPrincipal);
        width: 100%;
        color: var(--amarelo);
        font-weight: bold;
        border: 2px solid var(--pretoPrincipal);
        padding: 15px;
        font-size: 25px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }

    .submit-btn:hover{
        background-color: transparent;
        color: var(--pretoPrincipal);
    }
</style>