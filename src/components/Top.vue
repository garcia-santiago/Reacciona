<template>
  <h3> -- TOP SESIÓN -- </h3>
  <h5 v-for="resultado in resultados" v-bind:key="resultado">
    {{resultado}} ms
  </h5>
  
</template>

<script>
export default {
    props: ['resultados']
}
</script>

<style>

</style>