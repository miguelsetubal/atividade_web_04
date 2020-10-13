<template>
  <div>
     <h3>Nome:</h3>
    <input type="text" name="" id="" v-model="nome" /><br />
    <h3>Cargo:</h3>
    <input type="texte" name="" id="" v-model="cargo" /><br /><br />
    <h3>Data de Nascimento:</h3>
    <input type="date" name="" id="" v-model="dataNascimento" /><br /><br />
    <h3>Data de Entrada na Empresa:</h3>
    <input type="date" name="" id="" v-model="dataEmpresa" /><br /><br />
    <button @click="insertUser">Insert</button><br />
  </div>
</template>

<script>
export default {
  name: "UserInsert",
  data: function() {
    return {
      nome: "",
      cargo: "",
      dataNascimento: "",
      dataEmpresa: "",
      baseURI: "http://localhost:8080/server/api/funcs",
    };
  },
  methods: {
    insertUser: function() {
      let obj = {
       nome: this.nome,
        cargo: this.cargo,
        dataNascimento: this.dataNascimento,
        dataEmpresa: this.dataEmpresa,
      };

      this.$http.post(this.baseURI, obj).then((result) => {
        if (result.data != "") {
          this.$router.push({ name: 'Users'});
        } 
      });
    },
  },
};
</script>

<style></style>
