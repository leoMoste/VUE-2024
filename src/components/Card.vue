<script setup>
import { defineProps } from "vue";

defineProps({
  bg: {
    type: String,
    default: "bg- gray-100",
  },
});
</script>

<template>
  <div :class="`${bg} p-6 rounded-lg shadow-md`">
    <!--Slots in Vue.js allow you to pass content from a parent component to a child component-->
    <slot></slot>
    <!-- This is the placeholder for the passed content -->
  </div>
</template>
