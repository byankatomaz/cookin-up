<script lang="ts">
export default {
  props: {
    texto: String,
  },
};
</script>

<template>
  <button class="cor-botao">{{ texto }}</button>
</template>

<style scoped>
.cor-botao {
  color: var(--creme, #fffaf3);
  background: var(--coral, #f0633c);
  font-weight: 700;
  padding: 1rem 6rem;
  border-radius: 2rem;
}
</style>
