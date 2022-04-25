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

<style></style>
