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
  max-width: 70%;
  height: 30vh;
  margin-left: 15%;
  text-align: center;
}

#addTaskUI.dark {
  background-color: var(--dark-bg);
}
</style>
