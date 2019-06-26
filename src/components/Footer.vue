<template>
  <div class="footer">
    <a href="https://github.com/LegacyMode/Bremen-Mensa-Frontend">
      <img class="icon" src="../assets/GitHub-Mark-32px.png" alt="Github Logo"/>
    </a>
    |
    <a href="https://legacymo.de">legacymo.de</a>
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
.footer .icon {
  width: 16px;
  vertical-align: middle;
}
.footer a {
  color: black;
}
</style>
