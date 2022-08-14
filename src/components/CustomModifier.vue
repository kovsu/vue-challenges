<script setup lang="ts">
const props = defineProps<{
  type: string;
  // v-model 冒号后的字段
  title?: string;
  titleModifiers?: {
    capitalize: boolean;
  };

  // v-model 没有冒号后的字段
  modelValue?: string;
  modelModifiers?: {
    capitalize: boolean;
  };
}>();

const emit = defineEmits(["update:title", "update:modelValue"]);

function emitValue(e: Event) {
  let value = (e.target as HTMLInputElement).value;
  if (props.type === "default") {
    if (props.modelModifiers?.capitalize) {
      value = value.toUpperCase();
    }
    emit("update:modelValue", value);
  }

  if (props.type === "custom") {
    if (props.titleModifiers?.capitalize) {
      value = value.toLowerCase();
    }
    emit("update:title", value);
  }
}
</script>

<template>
  <input
    type="text"
    @input="emitValue"
    :value="type === 'default' ? modelValue : title"
  />
</template>
