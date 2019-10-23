<template>
  <div class="table">
    Aqui vai aparecer a tabela
    <div class="table-wrapper">
      <div class="table-header">
        <div class="header-cell">Nome</div>
        <div class="header-cell">Idade</div>
        <div class="header-cell">Sexo</div>
        <div class="header-cell">Morada</div>
        <div class="header-cell">Estado</div>
      </div>
      <div class="table-body">
        <div class="table-row" v-for="user in users">
          <div class="header-cell">{{user.Nome}}</div>
          <div class="header-cell">{{user.Idade}}</div>
          <div class="header-cell">{{user.Sexo}}</div>
          <div class="header-cell">{{user.Morada}}</div>
          <div class="header-cell">{{user.Estado}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    msg: String
  },
  data(){
    return {
      users: [
        {
          Nome: "Jose",
          Idade: 31,
          Sexo: "Masculino",
          Morada: "Na esquina",
          Estado: "Activo"
        },
        {
          Nome: "Maria",
          Idade: 24,
          Sexo: "Feminino",
          Morada: "Na esquina",
          Estado: "Activo"
        },
        {
          Nome: "Antonia",
          Idade: 60,
          Sexo: "Feminino",
          Morada: "Na esquina",
          Estado: "Activo"
        }
      ]
    };
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.table-wrapper{

  .table-header{
    display: flex;
    background-color: lightblue;

    .header-cell{
      width: calc(100% / 5);
      padding:10px 15px;
    }
  }

  .table-body{
    .table-row{
      display: flex;
      background-color:lightcoral;

      .header-cell{
        width: calc(100% / 5);
        padding:10px 15px;

      }
    }
  }
}
</style>
