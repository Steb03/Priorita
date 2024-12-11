<template>
  <div id="addTaskTextField" :class="theme">
    <input
      type="text"
      id="addTaskInput"
      placeholder="Add something to your day..."
      v-model="addTodo"
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
  background-color: var(--dark-bg);
  border-color: var(--border-color-dark);
  color: var(--dark-mode-text-color);
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
