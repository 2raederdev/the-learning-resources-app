<template>
  <TheHeader title="RememberMe"/>
  <TheResources />
</template>

<script>
import TheResources from './components/learning-resources/TheResources'
import TheHeader from './components/layouts/TheHeader'

export default {
  components: {
    TheHeader,
    TheResources
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 40px 0 0 0;
}
</style>