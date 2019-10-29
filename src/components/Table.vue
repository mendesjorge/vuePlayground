<template>
  <div class="table">
    Aqui vai aparecer a tabela
    <div class="table-wrapper">
      <div class="table-header">
        <div
          v-for="column in columnsConfiguration"
          :key="column.name"
          class="header-cell"
          :style="{'width':`${column.width}%`}"
        >
          {{column.display}}
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
    configurations: Array,
    data: Array
  },
  data(){
    return {
    }
  },
  computed: {
    columnsConfiguration() {
      console.log(this)
      // math to get table column width
      let columnWidth = 100 / this.configurations.reduce((prev, data) => prev + (data.columnWeight || 1), 0)

      return this.configurations.map(column => (
        {
          ...column,
          width: (columnWidth * (column.columnWeight || 1)).toFixed(2)
        }
      ))
    },
    rows() {
      return this.data.map( (row, index) => {
        return this.columnsConfiguration.map(column => (
          {
            uid:          `${column.attribute}-${index}`,
            value:        row[column.attribute],
            display:      column.valueMap && column.valueMap(row[column.attribute]),
            type:         column.type,
            width:        column.width
          }
        ))
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
