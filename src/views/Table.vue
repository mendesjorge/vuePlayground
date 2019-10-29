<template>
  <div class="table"
    :configurations="configurations"
    :data="users"
  >
    <app-table/>
  </div>
</template>

<script>
// @ is an alias to /src
import Table from '@/components/Table.vue'

export default {
  components: {
    "app-table": Table
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
      configurations: [
        {attribute: 'Nome', display: 'NAME', type: 'text', columnWeight: 3},
        {attribute: 'Idade', display: 'IDADE', type: 'text'},
        {attribute: 'Sexo', display: 'SEXO', type: 'text'},
        {attribute: 'Morada', display: 'MORADA', type: 'text',columnWeight: 6},
        {attribute: 'Estado', display: 'ESTADO', type: 'switch', valueMap: value => value? 'Activo':'Inactivo'}
      ]
    }
  }
}
</script>
