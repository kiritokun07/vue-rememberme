<template>
  <the-header title="RememberMe"></the-header>
  <the-resource></the-resource>
</template>

<script>
import TheHeader from "./components/layouts/TheHeader.vue";
import TheResource from "./components/learning-resources/TheResource.vue";

export default {
    components: {
      TheResource,
      TheHeader
    },
    data() {
        return {};
    }
}
</script>

<style>
*{
  box-sizing: border-box;
}

html{
  font-family: 'Roboto',sans-serif;
}

body{
  margin: 0;
}
</style>