<template>
    <h4>El tiempo de reacción fue: <span v-bind:class="score>=300 ? 'red':'green' " > {{score}} </span> ms</h4>
</template>

<script>
export default {
    props: ['score']
}
</script>

<style>
.green{
    color: green;
}
.red{
    color: red;
}
</style>