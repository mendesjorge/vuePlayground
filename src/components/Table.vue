<template>
  <div class="table">
    Aqui vai aparecer a tabela
    <div class="table-wrapper">
      <div class="table-header">
        <div
          v-for="name in header"
          :key="name"
          class="header-cell"
        >
          {{name}}
        </div>
      </div>
      <div class="table-body">
        <div
          class="table-row"
          v-for="(row, index) in rows"
          :key="index"
        >
          <app-table-row :row="row">
          </app-table-row>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TableRow from './TableRow.vue'
export default {
  components: {'app-table-row': TableRow},
  props: {
    msg: String
  },
  data(){
    return {
      header: [
        "Nome",
        "Idade",
        "Sexo",
        "Morada",
        "Estado"
      ],
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
  },
  computed: {
    rows() {
      return this.users.map( (user, index) => {
        let names = Object.getOwnPropertyNames(user)
        return names.map(name => ({
          value: user[name],
          uid: `${name}-${index}`,
          type:'text'
        }))
      })
    }
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
