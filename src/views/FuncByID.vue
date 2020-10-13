<template>
  <div>
    Id: <input type="text" name="" id="" v-model="id" /><br /><br />

    <button @click="fetchUserById">Buscar</button><br /><br />

    <p>Cod:{{ func.id }}</p>
    <p>Nome:{{ func.nome }}</p>
    <p>Cargo:{{ func.cargo }}</p>
    <p>Data de Nascimento:{{ func.dataNascimento }}</p>
    <p>Data de Entrada na Empresa:{{ func.dataEmpresa}}</p>

   
  </div>
</template>

<script>
export default {
  name: "Users",

  data() {
    return {
      id: 0,
      nome: "",
      cargo: "",
      dataNascimento: "",
      dataEmpresa: "",
      func: {},
      baseURI: "http://localhost:8080/server/api/funcs"
    };
  },
  methods: {
    fetchUserById: function() {
      this.$http
        .get(this.baseURI + "/" + this.id)
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
