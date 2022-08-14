<script setup lang="ts">
import { ref } from "vue";
import CustomModifier from "./components/CustomModifier.vue";
// import UpdateDom from "./components/UpdateDom.vue";
// import RefFamily from "./components/RefFamily.vue";

const value = ref("");
const value2 = ref("");
</script>

<template>
  <!-- <RefFamily></RefFamily> -->
  <!-- <UpdateDom></UpdateDom> -->
  <h1>小写</h1>
  <CustomModifier
    type="custom"
    v-model:title.capitalize="value2"
  ></CustomModifier>
  <h1>大写</h1>
  <CustomModifier type="default" v-model.capitalize="value"></CustomModifier>
</template>

<style scoped></style>
