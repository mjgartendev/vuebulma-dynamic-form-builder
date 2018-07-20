<template>
  <div class="field">
    <div class="control">
      <label class="label">{{ label }}</label>
      <input class="input" type="text" :name="name" :placeholder="placeholder" />
    </div>
  </div>
</template>

<script>
export default {
  name: "DateInput",
  props: ["label", "name", "placeholder"]
};
</script>
