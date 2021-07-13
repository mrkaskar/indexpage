<template>
  <div class="content g2-content">
    <object :data="url" type="application/pdf" name="file.pdf">
      <embed :src="url" type="application/pdf" />
    </object>
  </div>
</template>

<script>
import { decode64 } from "@utils/AcrouUtil";

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
          const decoded = decode64(this.$route.params.path);

          return decoded;
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
    /* height: -webkit-fill-available; */
    height: 100vh;
}
</style>