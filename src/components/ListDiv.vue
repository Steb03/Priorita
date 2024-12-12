<template>
  <div id="list-div" :class="theme">
  </div>
</template>

<script>
export default {
  props: ["theme"],
};
</script>

<style>
@import '/src/assets/base.css';

#list-div {
  width: 70vw;
  height: fit-content;
  padding-top: 50px;
  padding-bottom: 10px;
  border-radius: 4px;
  border-style: solid;
  border-width: 1px;
  transition: 0.2s ease all, left 0.2s cubic-bezier(0.18, 0.89, 0.35, 1.15);
}

#list-div.dark {
  border-color: var(--border-color-dark);
}
</style>
