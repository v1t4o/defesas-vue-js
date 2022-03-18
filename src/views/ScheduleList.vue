<template>
  <div>
    <v-row justify="center">
      <v-col sm="12" md="10">
        <v-card
          color="grey lighten-4"
          flat
          tile
        >
          <v-toolbar color="grey lighten-4" dense>
            <v-app-bar-nav-icon>
              <v-img
                max-height="30"
                max-width="30"
                src="http://www.fflch.usp.br/sites/fflch.usp.br/files/2019-11/06_fflch_simbolo.jpg"
              ></v-img>
            </v-app-bar-nav-icon>        

            <v-toolbar-title>FFLCH - Agendamentos - Pós-Graduação</v-toolbar-title>

            <v-spacer></v-spacer>
              
            <v-text-field 
              label="Buscar agendamentos" 
              v-model="term"
              hide-details
              single-line
            ></v-text-field>

            <v-btn icon>
              <v-icon>mdi-magnify</v-icon>
            </v-btn>

          </v-toolbar>
        </v-card>
      </v-col>
    </v-row>
    
    <v-row justify="center">
      <v-col>
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
