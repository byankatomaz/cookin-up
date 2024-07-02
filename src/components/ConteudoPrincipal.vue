<script lang="ts">
import SelecionarIngredientes from "./SelecionarIngredientes.vue";
import SuaLista from "./SuaLista.vue";
import Tag from "./Tag.vue";
import BotaoPrincipal from "./BotaoPrincipal.vue";
import MostrarReceitas from './MostrarReceitas.vue';

type Pagina = "SelecionarIngredientes" | "MostrarReceitas";

export default {
  components: { SelecionarIngredientes, Tag, SuaLista, BotaoPrincipal, MostrarReceitas },

  data() {
    return {
      ingredientes: [] as String[],
      conteudo: "SelecionarIngredientes" as Pagina,
    };
  },

  methods: {
    adicionarIngrediente(ingrediente: String) {
      this.ingredientes.push(ingrediente);
    },

    removerIngrediente(ingrediente: String) {
      this.ingredientes = this.ingredientes.filter((i) => i != ingrediente);
    },

    navegar(pagina: Pagina){
      this.conteudo = pagina;
    }
  },
};
</script>

<template>
  <main class="conteudo-principal">
    <SuaLista :ingredientes="ingredientes" />

    <SelecionarIngredientes v-if="conteudo === 'SelecionarIngredientes'"
      @adicionarIngrediente="adicionarIngrediente($event)"
      @removerIngrediente="removerIngrediente($event)"
      @buscarReceitas="navegar('MostrarReceitas')"
    />

    <MostrarReceitas v-else-if="conteudo === 'MostrarReceitas'" />

  </main>
</template>

<style scoped>
.conteudo-principal {
  padding: 6.5rem 7.5rem;
  border-radius: 3.75rem 3.75rem 0rem 0rem;
  background: var(--creme, #fffaf3);
  color: var(--cinza, #444);

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5rem;
}

@media only screen and (max-width: 1300px) {
  .conteudo-principal {
    padding: 5rem 3.75rem;
    gap: 3.5rem;
  }
}

@media only screen and (max-width: 767px) {
  .conteudo-principal {
    padding: 4rem 1.5rem;
    gap: 4rem;
  }
}
</style>
