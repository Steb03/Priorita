<script setup>
import { ref } from 'vue';

// Initialize reactive variable for focus state
let active = ref('not-active');

// Handle focus event
function onFocus() {
  active.value = 'active'; // Update the reactive reference using `.value`
}

// Handle blur event
function onBlur() {
  active.value = 'not-active'; // Update the reactive reference using `.value`
}

// Optional: If you want to bind this input to some parent data (addTodo), define it here.
const addTodo = ref('');
</script>

<template>
  <div id="addTaskTextField" :class="[theme, active]">
    <input
      type="text"
      id="addTaskInput"
      placeholder="Add something to your day..."
      v-model="addTodo" 
      @focus="onFocus"
      @blur="onBlur"
      :class="theme"
    />
  </div>
</template>

<script>
export default {
  props: ["theme"],
};
</script>

<style>
@import "/src/assets/base.css";

#addTaskTextField {
  display: inline;
  width: calc(fit-content + 10px);
  height: 37px;
  padding: 10px 0px 12px 0px;
  text-align: center;
  border-style: solid;
  border-width: 1px;
  border-radius: 5px;
  transition-duration: 0.2s;
}

#addTaskTextField.dark {
  color: white;
}

#addTaskTextField.dark.not-active {
  background-color: var(--dark-bg);
  border-color: var(--border-color-dark);
  color: var(--dark-mode-text-color);
}

.active {
  border-color: white;
}

input[type="text"]:focus {
  outline: none;
}

#addTaskInput {
  width: 80%;
  border: none;
  background-color: #0000;
  height: 100%;
  border-radius: 4px;
  border-width: 1px;
  font-size: 1em;
  margin: 2px;
  padding: 10px;
}

#addTaskInput.dark {
  color: var(--dark-mode-taxt-color);
}
</style>
