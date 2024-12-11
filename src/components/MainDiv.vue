<script setup>
import AddTaskUI from '@/components/AddTaskUI.vue';
</script>

<template>
  <div id="list-div" :class="theme">
    <h1 :class="theme">Start your day with a goal in mind.</h1>
    <AddTaskUI :theme="theme"/>
  </div>
</template>

<script>
export default {
  props: ["theme"],
};
</script>

<style>
@import '/src/assets/base.css';

div #list-div {
  width: 70vw;
  height: fit-content;
  padding-top: 50px;
  padding-bottom: 10px;
  position: absolute;
  top: 150px;
  left: 15vw;
  border-radius: 4px;
  border-style: solid;
  border-width: 1px;
  transition: 0.2s ease all, left 0.2s cubic-bezier(0.18, 0.89, 0.35, 1.15);
}

#list-div.dark {
  background-color: #242424;
  border-color: var(--border-color-dark);
}

h1 {
  font-weight: 300;
  text-align: center;
  margin-top: 20px;
  font-size: 2.7em !important;
  margin-bottom: 100px;
}

h1.dark {
  color: var(--dark-mode-text-color);
}

template {
  position: absolute;
  left: calc((70vw - 600px) / 2);
  width: 600px;
  height: 45px;
  border-style: solid;
  border-width: 1px;
  border-radius: 4px;
}
</style>
