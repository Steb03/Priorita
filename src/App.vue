<script setup>
import { ref, watch } from "vue";
import Navbar from "@/components/Navbar.vue";
import ListDiv from "@/components/ListDiv.vue";
import AddTaskUI from '@/components/AddTaskForm.vue';

let theme = ref("light");

watch(theme, (newTheme) => {
  if (newTheme === "dark") {
    document.body.classList.add("dark");
    document.body.classList.remove("light");
  } else {
    document.body.classList.add("light");
    document.body.classList.remove("dark");
  }
});
</script>

<template>
  <Navbar @theme="(t) => (theme = t)" />
  <main>
    <h1 :class="theme">Start your day with a goal in mind.</h1>
    <AddTaskUI :theme="theme"/>
    <ListDiv :theme="theme" />
  </main>
</template>

<script></script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Archivo+Narrow&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');
@import "/src/assets/base.css";

body {
  transition: 0.2s ease all;
  font-family: "Roboto", sans-serif;
}

body.dark {
  background-color: var(--dark-bg);
}

main {
  position: absolute;
  left: 15vw;
}

h1 {
  font-weight: 300;
  text-align: center;
  margin-top: 150px;
  font-size: 2.7em !important;
  margin-bottom: 100px;
  max-width: 70vw;
}

h1.dark {
  color: var(--dark-mode-text-color);
}
</style>
