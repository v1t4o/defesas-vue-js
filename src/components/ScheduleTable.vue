<template>
  <v-row justify="center">
    <v-col sm="12" md="10">
      <v-card dark>
        <v-card-title>
          Agendamentos - Defesas da Pós Graduação
        </v-card-title>
        <v-card-text>
          <v-simple-table>
            <thead>
              <tr>
                <th>Data e Horário</th>
                <th>Título</th>
                <th>Candidato(a)</th>
                <th>Nível</th>
                <th>Programa</th>
                <th>Orientador</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="schedule in schedules" :key="schedule.id">
                <td>{{ schedule.data_horario }}</td>
                <td>{{ schedule.titulo }}</td>
                <td>{{ schedule.nome }}</td>
                <td>{{ schedule.nivel }}</td>
                <td>{{ schedule.programa }}</td>
                <td>{{ schedule.orientador }}</td>
              </tr>
            </tbody>
          </v-simple-table>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>

</template>

<script>

export default{
  props: ['schedules']
}

</script>
