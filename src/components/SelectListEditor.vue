<template>
  <div class="field">
    <div class="control">
      <label class="label">SelectList Options</label>
      <input type="text" class="input" v-model="newOption" @keydown.enter="addOption" placeholder="New SelectList Option">
      <ul>
        <li 
          v-for="option in options"
          :key="option">
          {{option}}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "SelectListEditor",
  props: ["label", "multi", "options", "name"]
};
</script>
