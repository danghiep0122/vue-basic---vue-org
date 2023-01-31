<script>
export default {
  props: {
    msg: {
      type: String,
    },
  },
};
</script>

<template>
  <h2>{{ msg || "Hello, I'm Child" }}</h2>
</template>
