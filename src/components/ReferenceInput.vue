<template>
  <div class="field">
    <div class="control">
      <label class="label">{{ label }}</label>
      <input class="input" type="number" :name="name" :placeholder="placeholder" />
    </div>
  </div>
</template>

<script>
export default {
  name: "ReferenceInput",
  props: ["label", "name", "placeholder"]
};
</script>
