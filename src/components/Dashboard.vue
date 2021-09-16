<template>
  <div id="burger-table">
    <div>
      <div id="burger-table-heading">
        <div class="order-id">#:</div>
        <div>Cliente:</div>
        <div>Pão:</div>
        <div>Carne:</div>
        <div>Opcionais:</div>
        <div>Ações:</div>
      </div>
    </div>
    <div id="burger-table-rows">
      <div class="burger-table-row" v-for="dados in burgers" :key="dados.id" :value="dados.id">
        <div class="order-number">{{dados.id}}</div>
        <div>{{dados.nome}}</div>
        <div>{{dados.pao}}</div>
        <div>{{dados.carne}}</div>
        <div>
          <ul>
            <li v-for="(lista, index) in dados.opcionais" :key="index">{{lista}}</li>
          </ul>
        </div>
        <div>
          <select name="status" class="status" @change="atualizarPedido($event, dados.id)">
            <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="dados.status == s.tipo">{{s.tipo}}</option>
          </select>
          <button class="delete-btn" @click="deletarPedido(dados.id)">Cancelar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
  data(){
      return{
          burgers: null,
          burger_id: null,
          status: []
      }
  }, methods:{
      async getPedidos(){
          const req = await fetch("http://localhost:3000/burgers");

          const data = await req.json();

          this.burgers = data;

          console.log(data)

          // resgatar os status

          this.getStatus();

      },

        async getStatus(){
            const req = await fetch("http://localhost:3000/status");
            const data = await req.json();
            this.status = data;
        },

        async deletarPedido(id){
            const req = await fetch(`http://localhost:3000/burgers/${id}`,{
                method: "DELETE"
            });

            const res = await req.json();

            this.getPedidos()
        },

        async atualizarPedido(e, id){
            const option = e.target.value;
            const dataJson = JSON.stringify({status:option});

            const req = await fetch(`http://localhost:3000/burgers/${id}`, {
                method: "PATCH",
                headers: { "Content-Type": "application/json"},
                body: dataJson

            });

            const res = await req.json();

        },

  },mounted(){
      this.getPedidos()
  }
};
</script>

<style scoped>

#burger-table {
  max-width: 1200px;
  margin: 0 auto;
}

#burger-table-heading,
#burger-table-rows,
.burger-table-row {
  display: flex;
  flex-wrap: wrap;
}

#burger-table-heading {
  font-weight: bold;
  padding: 12px;
  border-bottom: 3px solid #333;
}

#burger-table-heading div,
.burger-table-row div{
  width: 19%;
}
.burger-table-row {
  width: 100%;
  padding: 12px;
  border-bottom: 1px solid #ccc;
}

#burger-table-heading .order-id,
.burger-table-row .order-number {
    width: 5%;
}

select {
    padding: 12px 6px;
    margin-right: 12px;
}

.delete-btn{
    background-color: var(--pretoPrincipal);
    color: var(--amarelo);
    font-weight: bold;
    border: 2px solid var(--pretoPrincipal);
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
}

.delete-btn:hover{
    background-color: transparent;
    color: var(--pretoPrincipal);
}

</style>