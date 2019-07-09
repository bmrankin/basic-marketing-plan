<template>
  <h3 :class="`${color} text-xl`">{{ text }}</h3>
</template>

<script>
export default {
  props: {
    text: String,
    color: {
      type: String,
      default: 'text-gray-600'
    }
  }
}
</script>
