<template>
  <div class="wishlist">
    <h1>Lista de desejos</h1>
    <CardProduto />
  </div>
</template>

<script>
// import ButtonCard from '@/components/buttonCard/ButtonCard.vue';
import CardProduto from '../components/card/CardProduto.vue';
export default {
  // name: WishList,
  components: {
    CardProduto
  },
  data() {
    return {
      produtos: [],
      estrelaFixa: 5,
      valorRealfixo: "123,99",
      valorDescontofixo:"99,99",
      listaDesejos: [],
      buttonCard: "cancel"
    }
  }
}
</script>
