<template>
  <div id="app">
      <Comparison use="Dusche" kwh="20" v-bind:curKWh="curKWh" v-on:change="update">
      {{text}}
      </Comparison>
    <Comparison use="Other" kwh="20" v-bind:curKWh="curKWh" v-on:change="update">
      {{text}}
      </Comparison>
  </div>
</template>

<script>
import Comparison from './components/Comparison.vue'


export default {
  name: 'app',
  components: {
    Comparison
  },
  data: function() {
      return {
          curKWh: 1,
          explanation: 'Wenn die Belegung bei {0}% liegt und Sie in einem {1} fahren.',
          occupancy: 60,
          traintype: 'Interregio'
      }
  },
  computed: {
    text: function () {
        return this.explanation.replace("{0}", this.occupancy).replace("{1}", this.traintype)
    },
    formula: function() {
        return this.value * (this.occupancy/60)
    }
  },
  methods: {
    update: function(event) {this.curKWh = event}
  }
}
</script>

<style>
    @import url('https://fonts.googleapis.com/css?family=Fira+Sans:400,400i,700');
    body {
        background-color: #454C4D;
        color: #fff;
        font-family: "Fira Sans", "Helvetica Neue", "Arial", sans-serif;
    }

    #app {
        max-width: 600px;
        margin: 0 auto;
    }
</style>
