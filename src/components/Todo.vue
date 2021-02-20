<template>
  <div class="tile flex-centered">
    <div class="tile-icon">
      <i class="icon icon-time"></i>
    </div>
    <div class="tile-content">
      <div class="tile-subtitle">{{ todo.description }}</div>
    </div>
    <div class="tile-action">
      <button class="btn btn-link">
        Done
      </button>
      <button class="btn btn-link">
        <span class="text-error">Remove</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped></style>
