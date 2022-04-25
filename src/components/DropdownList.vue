<template>
  <ul v-if="props.dropdownOpen" class="dropdown-list">
    <dropdown-item
      v-for="item in props.list"
      :key="item"
      :item="item"
      :query="props.query"
      @item-chosen="sendResult"
    />
  </ul>
</template>

<script lang="ts">
import DropdownItem from "./DropdownItem.vue";
export default {
  emits: ["item-chosen"],
  components: {
    DropdownItem,
  },
  props: {
    list: {
      required: true,
      type: Array,
    },
    dropdownOpen: {
      required: true,
      type: Boolean,
    },
    query: {
      required: true,
      type: String,
    },
  },
  setup(props, ctx) {
    function sendResult(item: string) {
      ctx.emit("item-chosen", item);
    }

    return { props, sendResult };
  },
};
</script>

<style scoped>
.dropdown-list {
  list-style: none;
  position: absolute;
  top: 150%;
  width: 20rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  background-color: var(--color-off);
}
</style>
