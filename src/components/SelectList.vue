<template>
  <div class="field">
    <div class="control">
      <label class="label">{{ label }}</label>
      <select class="select" :multiple="multi">
        <option 
          v-for="option in options"
          :key="option">
          {{option}}
        </option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: "SelectList",
  props: ["label", "multi", "options", "name"]
};
</script>
