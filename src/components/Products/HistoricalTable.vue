<template>
  <b-table
      :items="historicos"
      :fields="fields"
      striped hover responsive
  />
</template>

<script>
export default {
  name: "HistoricalTable",
  props: ['historicos'],
  data() {
    return {
      fields: ['estado', 'fechamostrar', 'descripcion', 'aclaracion', 'novedad'],
    }
  },
}
</script>

<style scoped>

</style>
