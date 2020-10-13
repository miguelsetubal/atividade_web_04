<template>
  <div>
    Cargo: <input type="text" name="" id="" v-model="cargo" /><br /><br />

    <button @click="fetchUserByCargo">Buscar</button><br /><br />

    <ul>
      <li v-for="func in func" :key="func.id">
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
  name: "FuncByCargo",

  data() {
    return {
      id: 0,
      nome: "",
      cargo: "",
      dataNascimento: "",
      dataEmpresa: "",
      func: [],
      baseURI: "http://localhost:8080/server/api/funcs"
    };
  },
  methods: {
    fetchUserByCargo: function() {
      this.$http
        .get(this.baseURI + "?cargo=" + this.cargo)
        .then(result => {
          this.func = result.data;
        })
        .catch(function(error) {
          console.log(error);
        });
        
        
    }
  }
};
</script>

<style></style>
