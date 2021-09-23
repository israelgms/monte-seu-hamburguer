<template>
  <div class="container">
    <div class="formLogin">
      <div class="image"><img src="/img/logo.png" alt="logo"></div>
        <h2>Bem vindo!!</h2>
        <h3>Digite seu e-mail e senha para continuar</h3>
      <form @submit="login">
        <div>
          <p>E-mail:</p>
          <input type="email" placeholder="Digite o seu e-mail" />
        </div>
        <div>
          <p>Senha:</p>
          <input type="password" placeholder="Digite sua senha" />
        </div>
        <div class="submit">
          <button>Entrar</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "LoginForm",
  data() {
    return {};
  },
  methods: {
    login(e) {
      e.preventDefault();
      alert("Funcionalidade em andamento");
    },
  },
};
</script>

<style scoped>
input {
  all: unset;
}

.image{
  background-color: var(--pretoPrincipal);
  border-radius: 50%;
  max-width: 150px;
  margin: 0 auto;
}

.container {
  width: 100%;
  height: 500px;
}

.formLogin {
  margin: 20px auto;
  text-align: center;
  width: 400px;
  height: 550px;
}

.formLogin h2{
  margin-top: 25px;
  color: var(--pretoPrincipal);
}

.formLogin h3{
  margin: 5px 0 30px 0;
  color: var(--pretoPrincipal);
}

.formLogin input {
  border: 1px solid var(--pretoPrincipal);
  width: 100%;
  height: 40px;
  margin-bottom: 10px;
}

input:focus {
  border: 1px solid var(--amarelo);
}

.submit button {
  border: 2px solid #141414;
  color: var(--amarelo);
  font-size: 25px;
  background-color: var(--pretoPrincipal);
  width: 100%;
  cursor: pointer;
  padding: 12px;
}
.submit button:hover {
  border: 2px solid #141414;
  color: var(--pretoPrincipal);
  background-color: transparent;
}

form p {
  text-align: left;
  font-weight: bold;
  margin-bottom: 5px;
}
</style>