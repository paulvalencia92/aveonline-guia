<template>
  <ValidationObserver v-slot="{ handleSubmit }">
    <b-form @submit.prevent="handleSubmit(searchData)">
      <b-row>

        <b-col cols="8">
          <ValidationProvider name="nombre" rules="required|numeric" v-slot="{ errors }">
            <b-form-group>
              <b-form-input placeholder="Escribe el numero de guia" v-model="guideNumber"></b-form-input>
            </b-form-group>
            <span class="text-danger">{{ errors[0] }}</span>
          </ValidationProvider>
        </b-col>

        <b-col cols="4">
          <b-button variant="danger" type="submit">
            Buscar
          </b-button>
        </b-col>
      </b-row>
    </b-form>
  </ValidationObserver>
</template>

<script>
import axios from 'axios'

export default {
  name: "FormSearch",
  data() {
    return {
      guideNumber: null,
      guides: [],
    }
  },
  methods: {
    async searchData() {
      const response = await axios.get('/estado_guia.php', {
        params: {
          guia: this.guideNumber
        }
      });
      this.$emit('setData', response.data)
    }
  }
}
</script>

<style scoped>

</style>
