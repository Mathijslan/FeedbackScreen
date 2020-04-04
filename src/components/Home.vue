<template>
  <v-container fluid>
    <v-container>
      <v-card>
        <v-layout v-for="data in room" justify-center align-center column pa-5>
          <div class="display-4 font-weight-black text-xs-center">CHECK-INS NEEDED FOR KBG1.11:</div>
          <div class="display-4 font-weight-black text-xs-center mb-3">{{data.checkins}}</div>
        </v-layout>
      </v-card>
    </v-container>
    <v-container>
      <v-card>
        <v-layout v-for="data in room" justify-center align-center column pa-5>
          <div class="display-4 font-weight-black text-xs-center mb-3">{{data.message}}</div>
        </v-layout>
      </v-card>
    </v-container>
  </v-container>
</template>

<script>
  export default {
    data() {
      return {
        search: ''
      }
    },
    computed: {
      loading() {
        return this.$store.getters.loading
      },
      filteredAudits() {
        return this.audits.filter((audit) => {
          return audit.title.toLowerCase().match(this.search.toLowerCase())
        })
      },
      room() {
        this.$store.dispatch('loadAudits')
        return this.$store.getters.loadedAudits
      }
    }
  }
</script>
