<template>
  <div class="row">
    <div
      class="header-cell"
      v-for="cell in row"
      :key="cell.uid"
    >
      <component
        :is="`table-${cell.type}-cell`"
        :cell="cell"
      ></component>
    </div>
  </div>
</template>

<script>
import TableTextCell from './TableTextCell'
export default {
  components: {
    'table-text-cell': TableTextCell
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
    display: flex;
    background-color: lightblue;

    .header-cell{
      width: calc(100% / 5);
      padding:10px 15px;
    }
  }
</style>
