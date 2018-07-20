<template>
<div class="field">
    <div class="control">
      <label class="label">Text Input Options</label>
      <input type="text" class="input" v-model="label" placeholder="Text Input Label">
    </div>
  </div>
</template>

<script>
export default {
  name: "TextInputEditor",
  props: ["label", "name", "placeholder"]
};
</script>
