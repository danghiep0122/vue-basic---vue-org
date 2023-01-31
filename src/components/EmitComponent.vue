<script setup>
const emit = defineEmits(["response"]);

emit("response", "Hello from Child");
</script>

<template><h2>Child component</h2></template>
