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
</style>
<style scoped>
/***************************************/
/*General*/
/***************************************/
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
