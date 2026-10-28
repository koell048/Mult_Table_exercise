<script setup>

const props = defineProps({
  labelText: {
    type: String,
    required: true,
  },
  inputType: {
    type: String,
    required: false,
    default: 'text',
  },
  min: {
    type: String,
    required: false,
  },
  max: {
    type: String,
    required: false,
  }
})
</script>

<template>
  <section class="input-field">
    <strong>{{ props.labelText }}</strong>
    <input :type="props.inputType"
           v-model="model"
           :min="props.min"
           :max="props.max"
    />
  </section>
</template>

<style scoped>
section.input-field {
  display: flex;
  gap: 20px;
  justify-content: space-between;
  width:100%;
  flex-direction: row;

  div {
    border: 1px solid black;
  }
}
</style>