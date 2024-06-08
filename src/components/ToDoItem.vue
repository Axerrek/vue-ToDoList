<template>
  <div class="itemList">
    <div class="checkboxes">
      <input type="checkbox" :checked="completed" @change="toggleComplete" />
    </div>
    <div class="text">
      <span :class="{ completed: completed }">{{ title }}</span>
    </div>
    <div class="buttons">
      <button @click="$emit('remove')">Usuń</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["title", "completed"],
  methods: {
    toggleComplete() {
      this.$emit("toggle-complete");
    },
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>
