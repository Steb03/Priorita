<script setup>
import { ref } from 'vue';

let active = ref('not-active');

function onFocus() {
  active.value = 'active';
}

function onBlur() {
  active.value = 'not-active'; 
}

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
  height: 37px;
  width: 100%;
  padding: 10px 0px 10px 0px;
  text-align: center;
  border-style: solid;
  border-width: 1px;
  border-radius: 5px;
  transition-duration: 0.1s;
}

#addTaskTextField.dark {
  color: white;
}

#addTaskTextField.dark.not-active {
  background-color: var(--dark-bg);
  border-color: var(--border-color-dark);
  color: var(--dark-mode-text-color);
}

#addTaskTextField.light.active {
  border-color: var(--theme-blue-green);
}

.active {
  border-color: white;
}

input[type="text"]:focus {
  outline: none;
}

#addTaskInput {
  width: calc(40vw - 40px);
  border: none;
  background-color: #0000;
  height: 17px;
  border-radius: 4px;
  border-width: 1px;
  font-size: 1em;
  margin: 2px;
  margin-top: 0px;
  padding: 10px;
}

#addTaskInput.dark {
  color: var(--dark-mode-text-color);
}
</style>
