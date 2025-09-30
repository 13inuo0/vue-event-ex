<template>
  <div class="container">
    <Event />
    <FormEx />
  </div>
</template>
<script setup>
import Event from "./components/Event.vue";
import FormEx from "./components/Form-ex.vue";
</script>

<style scoped>
.container{
    display: flex;
    gap: 20px;
}
.container div{
    flex: 1;
    background-color: antiquewhite;
}
</style>
