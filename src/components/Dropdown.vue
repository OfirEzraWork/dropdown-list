<template>
  <div class="dropdown">
    <dropdown-input
      @toggle-dropdown-list="toggleDropdownList"
      @search-input-changed="updateDropdownList"
      :placeholderText="props.placeholderText"
    ></dropdown-input>
    <dropdown-list
      :list="list"
      :dropdownOpen="dropdownOpen"
      :query="query"
      @item-chosen="sendResult"
    ></dropdown-list>
  </div>
</template>

<script lang="ts">
import { ref } from "vue";
import DropdownInput from "./DropdownInput.vue";
import DropdownList from "./DropdownList.vue";

export default {
  emits: ["item-chosen"],
  components: {
    DropdownInput,
    DropdownList,
  },
  props: ["placeholderText"],
  setup(props, ctx) {
    const query = ref("");
    const dropdownOpen = ref(false);
    const list = ref(["Barbarian", "Bard", "Cleric"]);

    function toggleDropdownList() {
      dropdownOpen.value = !dropdownOpen.value;
      console.log(dropdownOpen.value);
    }
    function closeDropdownList(e: Event) {
      if (!(e.target as Element).closest(".dropdown")) {
        dropdownOpen.value = false;
      }
      return;
    }
    function updateDropdownList(newQuery: string) {
      dropdownOpen.value = true;
      query.value = newQuery;
    }
    function sendResult(item: string) {
      dropdownOpen.value = false;
      ctx.emit("item-chosen", item);
    }

    return {
      //props
      props,
      //data
      query,
      dropdownOpen,
      list,
      //functions
      toggleDropdownList,
      closeDropdownList,
      updateDropdownList,
      sendResult,
    };
  },
};
</script>

<style></style>
