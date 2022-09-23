<template>
  <b-container>
    <FormSearch @setData="setData"/>
    <GuideDetails
        v-if="guide"
        class="mt-5"
        :guide="guide"/>
  </b-container>
</template>

<script>
import FormSearch from "./FormSearch";
import GuideDetails from "./GuideDetails";

export default {
  name: "Index",
  components: {
    FormSearch,
    GuideDetails
  },
  data() {
    return {
      guide: null
    }
  },
  methods: {
    setData(data) {
      if (data.type_error == '-99') {
        this.toast('NO SE ENCONTRO INFORMACIÓN', data.response)
        return;
      }
      this.guide = data.response.guias[0];
    },
    toast(title, text) {
      this.$bvToast.toast(text, {
        title,
        solid: true,
        variant: 'warning',
        autoHideDelay: 3000,
        toaster: 'b-toaster-top-center',
      })
    }
  }
}
</script>

<style scoped>

</style>
