<template>
  <Cabecalho />
  <Notificacao />
  <Carrinho />
  <router-view />
</template>

<style>
html {
  font-family: Arial;
}
</style>

<script>
import Carrinho from "./components/carrinhos/Carrinho.vue"
import Notificacao from "./components/layout/Notificacao.vue"
import Cabecalho from "./components/layout/Cabecalho.vue";

export default {
  components: {
    Carrinho,
    Notificacao,
    Cabecalho
  },
}
</script>