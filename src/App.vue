<template>
  <ApiGit />
</template>

<script>
import ApiGit from "./components/ApiGit.vue";

export default {
  name: 'App',
  components: {
    ApiGit
}
}
</script>

<style lang="scss">


*{
  padding: 0;
  margin: 0;
  font-family: "Poppins", sans-serif;
}

body{
  background-color: lightgray;
  display: flex;
  justify-content: center;
}
</style>
