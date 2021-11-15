<template>
  <input
    :type="type"
    class="p-3 w-full outline-none border text-sm text-gray-700 rounded my-2"
    :placeholder="placeholder"
    :required="required"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<script>
export default {
  name: "CustomInput",
  props: ["type", "placeholder", "required", "modelValue"],
};
</script>

<style></style>
