<script setup>
import { ref, defineEmits, watch, onMounted } from "vue";

const emit = defineEmits();

// Theme Scripts
let theme = ref("light");
let isChecked = ref(false);
let logoImageSrc = ref("/logo_dark.svg");

// Function to set a cookie
function setCookie(name, value, days) {
  const expires = new Date();
  expires.setTime(expires.getTime() + days * 24 * 60 * 60 * 1000); // Cookie expiration time
  document.cookie = `${name}=${value};expires=${expires.toUTCString()};path=/`;
}

// Function to get a cookie by name
function getCookie(name) {
  const nameEQ = `${name}=`;
  const ca = document.cookie.split(";");

  for (let i = 0; i < ca.length; i++) {
    let c = ca[i];
    while (c.charAt(0) === " ") c = c.substring(1, c.length); // trim leading spaces
    if (c.indexOf(nameEQ) === 0) return c.substring(nameEQ.length, c.length);
  }
  return null;
}

// Check if a theme is already set in the cookies on mount
onMounted(() => {
  const savedTheme = getCookie("theme");
  if (savedTheme) {
    theme.value = savedTheme;
    isChecked.value = savedTheme === "dark"; // Set checkbox based on theme
  }
});

// Watch the checkbox for changes and update the theme accordingly
watch(isChecked, (newValue) => {
  theme.value = newValue ? "dark" : "light";
  setCookie("theme", theme.value, 365); // Save theme in cookie for 365 days
  emit("theme", theme.value);
});

</script>

<template>
  <nav :class="theme">
    <ul>
      <li><img src="/public/logo_blue.svg"height="30px" id="logo-nav" /></li>
      <li>
        <div class="button r" id="button-3">
          <input v-model="isChecked" type="checkbox" class="checkbox" />
          <div class="knobs"></div>
          <div class="layer"></div>
        </div>
      </li>
    </ul>
  </nav>
</template>

<style>
@import "/src/assets/base.css";

li {
  list-style-type: none;
  display: inline;
}

nav {
  position: absolute;
  width: 100vw;
  height: 55px;
  left: 0;
  top: 0;
  border-bottom-style: solid;
  border-bottom-width: 1px;
  transition: 0.3s ease all, left 0.3s cubic-bezier(0.18, 0.89, 0.35, 1.15);
}

nav.dark {
  color: white;
  border-color: var(--border-color-dark);
}

nav.light {
  background-color: var(--nav-light-color);
  color: rgb(0, 0, 0);
  border-color: #000;
}

#logo-nav {
  position: absolute;
  top: calc((55px - 30px) / 2);
  left: 20px;
}

/* Button 3 */
#button-3 .knobs:before {
  content: "";
  position: absolute;
  top: 3px;
  left: 4px;
  width: 11px;
  height: 1px;
  color: #fff;
  font-size: 10px;
  font-weight: bold;
  text-align: center;
  line-height: 1;
  padding: 9px 4px;
  background-color: #fff;
  border-radius: 50%;
  transition: 0.3s ease all, left 0.3s cubic-bezier(0.18, 0.89, 0.35, 1.15);
}

#button-3 .checkbox:active + .knobs:before {
  width: 30px;
  border-radius: 100px;
}

#button-3 .checkbox:checked:active + .knobs:before {
  margin-left: -20px;
}

#button-3 .checkbox:checked + .knobs:before {
  content: "";
  left: 33px;
  background-color: #232323;
}

#button-3 .checkbox:checked ~ .layer {
  background-color: var(--theme-main);
  border-color: var(--theme-main);
}

#button-3 .checkbox ~ .layer {
  background-color: var(--theme-blue-green);
}

.button-cover,
.knobs,
.layer {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

.button {
  position: absolute;
  top: calc((55px - 25px) / 2);
  right: 20px;
  width: 55px;
  height: 25px;
  overflow: hidden;
}

.button.r,
.button.r .layer {
  border-radius: 100px;
}

.button.b2 {
  border-radius: 2px;
}

.checkbox {
  position: relative;
  width: 100%;
  height: 100%;
  padding: 0;
  margin: 0;
  opacity: 0;
  cursor: pointer;
  z-index: 3;
}

.knobs {
  z-index: 2;
}
</style>
