<template>
  <div class="table">
    Aqui vai aparecer a tabela
    <div class="table-wrapper">
      <div class="table-header">
        <div
          v-for="config in configs"
          :key="config.name"
          class="header-cell"
          :style="{'width':`${config.width}%`}"
        >
          {{config.display}}
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
      users: [
        {
          Nome: "Jose",
          Idade: 31,
          Sexo: "Masculino",
          Morada: "Na esquina",
          Estado: true
        },
        {
          Nome: "Maria",
          Idade: 24,
          Sexo: "Feminino",
          Morada: "Na esquina",
          Estado: true
        },
        {
          Nome: "Antonia",
          Idade: 60,
          Sexo: "Feminino",
          Morada: "Na esquina",
          Estado: false
        }
      ],
      columns: [
        {attribute: 'Nome', display: 'NAME', type: 'text', columnWeight: 3},
        {attribute: 'Idade', display: 'IDADE', type: 'text'},
        {attribute: 'Sexo', display: 'SEXO', type: 'text'},
        {attribute: 'Morada', display: 'MORADA', type: 'text',columnWeight: 6},
        {attribute: 'Estado', display: 'ESTADO', type: 'switch', valueMap: value => value? 'Activo':'Inactivo'}
      ]
    };
  },
  computed: {
    configs() {
      // math to get table column width
      let columnWidth = 100 / this.columns.reduce((prev, data) => prev + (data.columnWeight || 1), 0)

      let ret =  this.columns.map(column => (
        {
          ...column,
          width: (columnWidth * (column.columnWeight || 1)).toFixed(2)
        }
      ))
      console.log(ret)
      return ret
    },
    rows() {
      let rows = this.users.map( (row, index) => {

        return this.configs.map(config => (
          {
            uid:          `${config.attribute}-${index}`,
            value:        row[config.attribute],
            display:      config.valueMap && config.valueMap(row[config.attribute]),
            type:         config.type,
            width:        config.width
          }
        ))
      })
      return rows
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
      padding:10px 15px;
    }
  }

  .table-body{
    .table-row{
      display: flex;
      background-color:lightcoral;

      .header-cell{

        padding:10px 15px;

      }
    }
  }
}
</style>
