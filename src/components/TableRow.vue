<template>
  <div class="row">
    <div
      class="header-cell"
      v-for="cell in row"
      :key="cell.uid"
      :style="{'width': `${cell.width}%`}"
    >
      <component
        :is="`table-${cell.type}-cell`"
        :cell="cell"
      ></component>
    </div>
  </div>
</template>

<script>
import TableTextCell from './TableTextCell.vue'
import TableSwitchCell from './TableSwitchCell.vue'
export default {
  components: {
    'table-text-cell': TableTextCell,
    'table-switch-cell': TableSwitchCell,

  },
  props: {
    row: Array
  },
  data(){
    return {
    }
  }
}
</script>

<style scoped lang="scss">
  .row{
    width: 100%;
    display: flex;
    background-color: lightblue;

    .header-cell{
      padding:10px 15px;
    }
  }
</style>
