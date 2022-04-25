<template>
  <li
    v-if="props.item.toLowerCase().includes(props.query)"
    class="dropdown-list-item"
  >
    <button class="list-item-button" @click="sendResult">
      {{ props.item }}
    </button>
  </li>
</template>

<script lang="ts">
export default {
  emits: ["item-chosen"],
  props: {
    item: {
      required: true,
      type: String,
    },
    query: {
      required: true,
      type: String,
    },
  },
  setup(props, ctx) {
    function sendResult() {
      ctx.emit("item-chosen", props.item);
    }
    return { props, sendResult };
  },
};
</script>

<style scoped>
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
</style>
