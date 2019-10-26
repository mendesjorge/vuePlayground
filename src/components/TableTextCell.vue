<template>
  <span
    :style="{'width': `${cellWidth}px`}"

  > {{cell.value}} </span>
</template>
<script>
export default {
  props:{
    cell: Object
  },
  computed:{
    cellWidth(){
      return 100/Object.getOwnPropertyNames(this.cell).length
    }
  }
}
</script>
