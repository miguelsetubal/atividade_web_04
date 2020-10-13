<template>
  <div>
    <h3>Nome:</h3>
    <input type="text" name="" id="" v-model="func.nome" /><br />
    <h3>Cargo:</h3>
    <input type="texte" name="" id="" v-model="func.cargo" /><br /><br />
    <h3>Data de Nascimento:</h3>
    <input type="date" name="" id="" v-model="func.dataNascimento" /><br /><br />
    <h3>Data de Entrada na Empresa:</h3>
    <input type="date" name="" id="" v-model="func.dataEmpresa" /><br /><br />
    <button @click="editRegister">Edit</button><br />
  </div>
</template>

<script>
export default {
  name: "UserEdit",
  props: ["id"],
  data: function() {
    return {
      func: {},
      baseURI: "http://localhost:8080/server/api/funcs",
    };
  },
  created: function() {
    this.$http
      .get(this.baseURI + "/" + this.id)
      .then((result) => {
        this.func = result.data;
      })
      .catch(function(error) {
        console.log(error);
      });
  },
  methods: {
    editRegister: function() {
      let obj = {
        nome: this.func.nome,
        cargo: this.func.cargo,
        dataNascimento: this.func.dataNascimento,
        dataEmpresa: this.func.dataEmpresa,
      };

      this.$http.put(this.baseURI + "/" + this.id, obj).then((result) => {
        this.$router.push({ name: 'Users'});
      });
    },
  },
};
</script>

<style></style>
