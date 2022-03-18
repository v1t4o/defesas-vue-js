<template>
  <v-row justify="center">
    <v-col sm="12" md="10">
      <v-card color="grey lighten-4">
        <v-card-title>
          Agendamentos - Defesas da Pós Graduação
        </v-card-title>
        <v-card-text>
          <v-data-table
            :headers="headers"
            :items="schedules"
            :items-per-page="20"
            class="elevation-1"
          >
          </v-data-table>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>

</template>

<script>

export default{
  props: ['schedules'],
  data () {
    return {
      headers: [
        {text: 'Data e Horário', value: 'data_horario'}, 
        {text: 'Título', value: 'titulo'}, 
        {text: 'Candidato(a)', value: 'nome'}, 
        {text: 'Nível', value: 'nivel'}, 
        {text: 'Programa', value: 'programa'}, 
        {text: 'Orientador', value: 'orientador'}
      ]
    }
  },
}

</script>
