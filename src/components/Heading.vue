<template>
  <h2 :class="`${color} text-2xl`">{{ text }}</h2>
</template>

<script>
export default {
  props: {
    text: String,
    color: {
      type: String,
      default: 'text-gray-800'
    }
  }
}
</script>
