<script setup lang="ts">
import { ref, nextTick } from "vue";

withDefaults(
  defineProps<{
    str: string;
  }>(),
  {
    str: "aa",
  }
);

const count = ref(0);
const counter = ref<HTMLButtonElement | null>(null);

function increment() {
  count.value++;

  /**
   * DOM is not yet updated, how can we make sure that the DOM gets updated
   * Make the output be true
   */
  nextTick(() => {
    console.log("DOM 更新之后");
    console.log(+counter!.value!.textContent! === 1);
  });
}
</script>

<template>
  {{ str }}
  <button ref="counter" @click="increment">
    {{ count }}
  </button>
</template>
