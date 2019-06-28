<template>
    <article>
        <h1>{{use}}</h1>
        <h2><span class="value-label">Distanz:</span>&nbsp;<input type="text" v-model="value"/> km </h2>
        <p class="explanation"><slot></slot></p>
        <p>{{curKWh}}</p>
    </article>
</template>

<script>
export default {
  name: 'Comparison',
  props: ['use', 'kwh', 'curKWh'],
  data: function() {
    return {
        currentKWh: this.kwh
    }
  },
  computed: {
      value: {
        get: function () {
          return parseInt(this.curKWh) / 2 
        },
        set: function (val) {
           this.$emit('change', parseInt(val) ? parseInt(val)*2 : 0) 
        }
      }
  }
}
</script>

<style scoped>
    .value-label {
        font-family: serif;
        font-style: italic;
    }

    .explanation {
        font-family: serif;
        font-style: italic;
    }
</style>
