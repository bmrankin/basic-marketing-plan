<template>
  <div>
    <span v-if="label" class="text-gray-400 text-sm">
      {{ label }}
    </span>
    <input 
      type="text"
      :value="value"
      :class="`bg-white focus:outline-none focus:border focus:border-blue-600 border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal ${fontSize}`"
      v-on:input="$emit('input', $event.target.value)"

    />
  </div>
</template>

<script>
export default {
  props: {
    value: String,
    fontSize: {
      type: String,
      default: 'text-base'
    },
    label: {
      type: String,
      default: null
    }
  }
}
</script>
