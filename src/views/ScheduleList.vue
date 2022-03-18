<template>
  <div>
    <v-row justify="center">
      <v-col sm="12" md="10">
        <v-text-field label="Buscar agendamentos" v-model="term"></v-text-field>
        <ScheduleTable :schedules="filterSchedules"/>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import ScheduleTable from '@/components/ScheduleTable.vue'

export default ({
  name: 'ScheduleList',
  components: {
    ScheduleTable
  },
  data () {
    return {
      schedules: [],
      term: ''
    }
  },

  async mounted () {
    this.schedules = await this.getSchedules()
  },

  methods: {
    async getSchedules () {
      const response = await fetch('https://defesas.fflch.usp.br/api/agendamentos')
      console.log(response);
      return response.json()
    }
  },
  computed: {
    filterSchedules () {
      return this.schedules.filter((schedules) => schedules.nome.toLowerCase().includes(this.term.toLowerCase()))
    }
  }
})
</script>
