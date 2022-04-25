<template>
  <div class="container" @click="closeDropdownList">
    <dropdown
      @item-chosen="retrieveData"
      :placeholderText="placeholderText"
    ></dropdown>
    <p class="result">{{ chosenItem }}</p>
  </div>
</template>

<script lang="ts">
import { ref } from "vue";
import Dropdown from "./components/Dropdown.vue";
export default {
  components: {
    Dropdown,
  },
  setup() {
    const placeholderText = "Search or choose";

    const chosenItem = ref("");
    function retrieveData(item: string) {
      chosenItem.value = item;
    }

    return { chosenItem, retrieveData, placeholderText };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html {
  font-size: 62.5%;
}
body {
  font-family: "Jost", sans-serif;
  line-height: 1;
  /* color: ; */
}

:root {
  --color-main: #1b995e;
  --color-off: #8ddba4;
}

/***************************************/
/*General*/
/***************************************/
main {
  /* max-width: 144rem;
  height: 50vh;
  margin: 16rem auto 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center; */
}

.visible {
  visibility: hidden;
}

.container {
  max-width: 144rem;
  padding: 16rem;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

/***************************************/
/*dropdown*/
/***************************************/

.dropdown {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  position: relative;
  width: 20rem;
  padding-left: 1.2rem;
  margin-bottom: 40rem;
  background-color: var(--color-off);
  display: grid;
  grid-template-columns: 14rem 1fr;
  align-items: center;
}
.dropdown-input {
  font-family: inherit;
  height: 3.5rem;

  background-color: var(--color-off);
  border: none;
}
.icon-button {
  background-color: inherit;
  border: none;
  height: 100%;
  width: 100%;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}
.dropdown-icon {
  font-size: 1.8rem;
}

/***************************************/
/*dropdown-list*/
/***************************************/

.dropdown-list {
  list-style: none;
  position: absolute;
  top: 150%;
  width: 20rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  background-color: var(--color-off);
}
.dropdown-list-item {
  cursor: pointer;
}
.dropdown-list-item:nth-child(odd) {
  background-color: var(--color-main);
}
.list-item-button {
  cursor: inherit;
  padding: 0.8rem 1.2rem;
  height: 100%;
  width: 100%;
  text-align: left;
  font: inherit;
  font-size: 1.6rem;
  background-color: inherit;
  border: none;
}

/***************************************/
/*Result*/
/***************************************/
.result {
  width: 20rem;
  min-height: 3.2rem;
  padding: 0.8rem 1.2rem;
  font-size: 1.6rem;
  background-color: var(--color-main);
}
</style>
