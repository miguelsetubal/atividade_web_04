<template>
  <div class="home">
    <ul>
      <li v-for="func in funcs" :key="func.id">
       <h4>{{ func.id }}</h4>
            <h4>Cod. Funcionário: {{ func.id }}</h4>
            <p>Nome: {{ func.nome }}</p>
            <p>Cargo: {{ func.cargo }}</p>
            <p>Data de Nascimento: {{ func.dataNascimento }}</p>
            <p>Data de Entrada na Empresa: {{ func.dataEmpresa }}</p>
        <hr />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      funcs: [],
      baseURI: "http://localhost:8080/server/api/funcs",
    };
  },
  created: function() {
    this.$http.get(this.baseURI).then((result) => {
      this.funcs = result.data;
    });
  },
};
</script>
