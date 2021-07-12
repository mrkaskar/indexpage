<template>
  <div class="content g2-content">
    <vue-pdf-app :pdf="url"></vue-pdf-app>
  </div>
</template>

<script>
import { decode64 } from "@utils/AcrouUtil";
import VuePdfApp from "vue-pdf-app";

export default {
  components: {
    VuePdfApp
  },
  data: function() {
    return {};
  },
  computed: {
    url() {
      if (this.$route.params.path) {
        return decode64(this.$route.params.path);
      }
      return ''
    }
  },
  methods: {}
};
</script>

<style scoped>
object{
    width: 100%;
    height: -webkit-fill-available;
}
</style>