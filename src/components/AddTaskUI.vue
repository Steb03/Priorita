<script setup>
import AddTaskTextInput from '@/components/AddTaskTextInput.vue';
</script>

<template>
  <div id="addTaskUI" :class="theme">
    <AddTaskTextInput :theme="theme" />
  </div>
</template>

<script>
export default {
  props: ["theme"],
};
</script>

<style>
@import "/src/assets/base.css";

#addTaskUI {
  width: 70%;
  height: 30vh;
  text-align: center;
  padding: 5px;
  border-style: solid;
  border-width: 1px;
  border-radius: 4px;
  margin-left: calc((70vw - 70%) / 2)
}

#addTaskUI.dark {
  background-color: var(--lighter-dark-bg);
  border-color: var(--border-color-dark);
}
</style>
