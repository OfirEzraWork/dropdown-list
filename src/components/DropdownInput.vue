<template>
  <input
    v-model="query"
    :placeholder="placeholderText"
    class="dropdown-input"
    type="text"
  />
  <button @click="$emit('toggle-dropdown-list')" class="icon-button">
    <ion-icon class="dropdown-icon" name="chevron-down-outline"></ion-icon>
  </button>
</template>

<script>
export default {
  props: ["placeholderText"],
  emits: ["toggle-dropdown-list", "search-input-changed"],
  watch: {
    query() {
      this.$emit("search-input-changed", this.query);
    },
  },
  data() {
    return {
      query: "",
    };
  },
};
</script>

<style scoped>
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
</style>
