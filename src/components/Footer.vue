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
    margin: 1rem 0;
    margin-bottom: 30px; 
    text-align: right;
  }
  .footer a {
    color: black;
  }
</style>
