<template>
  <div class="table">
    <app-table/>
  </div>
</template>

<script>
// @ is an alias to /src
import Table from '@/components/Table.vue'

export default {
  components: {
    "app-table": Table
  }
}
</script>
