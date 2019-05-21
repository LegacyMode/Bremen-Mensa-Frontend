<template>
  <div class="footer">
    <a  href="https://legacymo.de">legacymo.de</a>
  </div>
</template>

<script>

export default {
  name: "Footer",
  components: {},
  props: {
    plan: {}
  }
};
</script>

<style scoped>
  .footer {
    clear: both;
  }
  .footer a {
    color: black;
    float:right;
  }
</style>
