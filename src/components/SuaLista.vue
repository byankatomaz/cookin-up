<script lang="ts">
import Tag from './Tag.vue';

export default {
  components: { Tag },
  props: {
    ingredientes: { type: Array, required: true }
  }
};
</script>

<template>
  <section>
    <span class="subtitulo-lg sua-lista-texto"> Sua lista: </span>
    <ul class="ingredientes-sua-lista" v-if="ingredientes.length">
      <li v-for="ingrediente in ingredientes" :key="ingrediente">
        <Tag :texto="ingrediente" ativa />
      </li>
    </ul>

    <p v-else class="paragrafo lista-vazia">
      <img src="../assets/images/sem-receitas.png" alt="" height="120px" width="120px" />
      Sua lista esta vazia, selecione ingredientes para iniciar.
    </p>
  </section>
</template>

<style scoped>
.sua-lista-texto {
  color: var(--coral, #f0633c);
  display: block;
  text-align: center;
  margin-bottom: 1.5rem;
}

.ingredientes-sua-lista {
  display: flex;
  justify-content: center;
  gap: 1rem 1.5rem;
  flex-wrap: wrap;
}

.lista-vazia {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.25rem;

  color: var(--coral, #f0633c);
  text-align: center;
}

</style>
