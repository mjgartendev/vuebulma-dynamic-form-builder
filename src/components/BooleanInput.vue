<template>
  <div class="field">
    <div class="control">
      <label class="label">{{ label }}</label>
      <input class="input" type="boolean" :name="name" :placeholder="placeholder" />
    </div>
  </div>
</template>

<script>
export default {
  name: "BooleanInput",
  props: ["label", "name", "placeholder", "type"]
};
</script>
