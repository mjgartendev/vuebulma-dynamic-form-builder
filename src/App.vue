<template>
  <div id="app">
    <header class="navbar">
    <h1 class="title is-3">Vue Dynamic Forms</h1>
    </header>
    
    <div class="columns">      
      <div id="form-edit" class="column is-two-fifths">
      <span class="title is-4">Field Editor</span>
        <div class="box" v-for="item in schema"
          :key="item.name">

        <h4 class="title is-4">{{item.name}}</h4>
        <hr>
          
          <div class="field">
          <label class="label">Field Type</label>
            <div class="control">
              <div class="select">
                <select name="fieldType" v-model="item.fieldType">
                  <option v-for="option in fieldTypes" :key="option">{{option}}</option>
                </select>
              </div>
            </div>
          </div>

          <div class="field">            
            <label class="label">Label</label>
            <div class="control">       
              <input class="input" type="text" v-model="item.label">
            </div>
          </div>

          <div class="field">            
            <label class="label">Placeholder</label>
            <div class="control">
              <input class="input" name="placeholder" type="text" v-model="item.placeholder">
            </div>
          </div>
          
          <template v-if="item.fieldType == 'SelectList'">
            <div class="field">
              <label class="label">Options</label>
              <div class="control">
                <input class="input" name="newOption" type="text" v-model="item.newOption">
                <button class="button is-success" type="button" @click.prevent="addOption">+</button>
              </div>
              <ul>
              <li v-for="option in item.options" :key="option">
              {{option}} <span class="icon is-pulled-right" @click.prevent="deleteOption"><i class="delete"></i></span>
              </li>
              </ul>
            </div>
             <div class="field">
              <label class="label">Select Multiple?</label>
              <div class="control">
                <input class="checkbox" name="isMultiselect" type="checkbox" v-model="item.multi">
              </div>
            </div>
          </template>
        </div>
      </div>

      <div id="form-preview" class="column">
        <span class="title is-4">Form Preview</span>
        <form class="form box">
          <component 
            v-for="(field, index) in schema"
            :key="index"
            :is="field.fieldType"
            v-bind.sync="field">
          </component>
        </form>
      </div>

    </div>
  </div>
</template>

<script>
import TextInput from "./components/TextInput";
import SelectList from "./components/SelectList";
import NumberInput from "./components/NumberInput";
import BooleanInput from "./components/ObjectInput";
import ReferenceInput from "./components/ReferenceInput";
import ArrayInput from "./components/ArrayInput";
import ObjectInput from "./components/ObjectInput";
import DateInput from "./components/DateInput";
import TimeInput from "./components/TimeInput";

export default {
  name: "App",
  components: {
    TextInput,
    SelectList,
    NumberInput,
    BooleanInput,
    ObjectInput,
    ArrayInput,
    ReferenceInput,
    DateInput,
    TimeInput
  },
  data() {
    return {
      schema: [
        {
          fieldType: "SelectList",
          name: "fieldType",
          multi: false,
          label: "Field Type",
          options: [
            "TextInput",
            "SelectList",
            "NumberInput",
            "BooleanInput",
            "ObjectInput",
            "ArrayInput",
            "ReferenceInput",
            "DateInput",
            "TimeInput"
          ]
        },
        {
          fieldType: "TextInput",
          placeholder: "Field Name",
          label: "Field Name",
          name: "field-name"
        },
        {
          fieldType: "TextInput",
          placeholder: "Field Label",
          label: "Field Label",
          name: "field-label"
        },
        {
          fieldType: "BooleanInput",
          name: "field-is-required",
          label: "Required?",
          default: false,
          value: false
        }
      ],
      fieldTypes: [
        "TextInput",
        "SelectList",
        "NumberInput",
        "BooleanInput",
        "ObjectInput",
        "ArrayInput",
        "ReferenceInput",
        "DateInput",
        "TimeInput"
      ]
    };
  },
  methods: {
    deleteOption() {}
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-color: #f1f1f1;
  padding: 2%;
}

#form-edit {
  overflow: auto;
}

#form-preview {
  overflow: none;
}
</style>
