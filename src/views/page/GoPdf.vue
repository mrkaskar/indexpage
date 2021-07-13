<template>
  <div class="content g2-content">
    <vue-pdf-app :pdf="url"></vue-pdf-app>
  </div>
</template>

<script>
import { decode64 } from "@utils/AcrouUtil";
import VuePdfApp from "vue-pdf-app";

function base64ToArrayBuffer(base64) {
  var binary_string = window.atob(base64);
  var len = binary_string.length;
  var bytes = new Uint8Array(len);
  for (var i = 0; i < len; i++) {
    bytes[i] = binary_string.charCodeAt(i);
  }
  return bytes.buffer;
}

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
          return base64ToArrayBuffer(this.$$route.params.path);
        //return decode64(this.$route.params.path);
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