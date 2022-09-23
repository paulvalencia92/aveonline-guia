<template>
  <div>
    <b-card
        border-variant="danger"
        header="INFORMACIÓN DE LA GUIA"
        header-bg-variant="danger"
        header-text-variant="white"
        align="center"
    >
      <b-card-body class="p-4">


        <b-list-group>
          <b-list-group-item><b>Destinatario: </b> {{ guide.destinatario }}</b-list-group-item>
          <b-list-group-item><b>Telefono: </b> {{ guide.telefono }}</b-list-group-item>
          <b-list-group-item><b>Direccion: </b> {{ guide.direccion }}</b-list-group-item>
          <b-list-group-item><b>Estado: </b> {{ guide.estado }}</b-list-group-item>
          <b-list-group-item><b>Origen: </b> {{ guide.origen }}</b-list-group-item>
          <b-list-group-item><b>Destino: </b> {{ guide.destino }}</b-list-group-item>
          <b-list-group-item><b>Fecha entrega: </b> {{ guide.dsfechaentrega }}</b-list-group-item>
        </b-list-group>

        <!--      {"estado":"","fechamostrar":"2022-09-16 14:00:15","descripcion":" (undefined)","aclaracion":"","novedad":"0"}-->

        <div class="text-right mt-4">
          <b-button
              v-if="guide.historicos.length"
              @click="showModalHistoricos"
              variant="outline-secondary"
              size="lg"
              class="mr-2">
            Ver historico
          </b-button>
          <a download
             :href="guide.rutadigitalizada"
             class="btn btn-lg btn-outline-danger">
            Descargar
          </a>

        </div>

      </b-card-body>

    </b-card>

    <!--============================
        Modal historico
    ==============================-->
    <b-modal ref="modal-historico" title="Historial" size="lg" hide-footer>
      <HistoricalTable :historicos="guide.historicos"/>
    </b-modal>

  </div>

</template>

<script>
import HistoricalTable from "./HistoricalTable";

export default {
  name: "GuideDetails",
  props: ['guide'],
  components: {
    HistoricalTable
  },
  data() {
    return {
      historicos: [
        {estado: "", fechamostrar: "2022-09-16 14:00:15", descripcion: "(undefined)", aclaracion: "", novedad: "0"},
        {estado: "", fechamostrar: "2022-09-16 14:00:15", descripcion: "(undefined)", aclaracion: "", novedad: "0"},
        {estado: "", fechamostrar: "2022-09-16 14:00:15", descripcion: "(undefined)", aclaracion: "", novedad: "0"},
        {estado: "", fechamostrar: "2022-09-16 14:00:15", descripcion: "(undefined)", aclaracion: "", novedad: "0"},
        {estado: "", fechamostrar: "2022-09-16 14:00:15", descripcion: "(undefined)", aclaracion: "", novedad: "0"},
      ]
    }

  },
  methods: {
    showModalHistoricos() {
      this.$refs['modal-historico'].show();
    }
  }
}
</script>

<style scoped>

</style>
