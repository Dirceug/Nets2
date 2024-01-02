<template>
  <div class="home">
    <CardProduto 
      :produtosArray="produtos" 
      :valorRealComponent="valorRealfixo" 
      :valorDescontoComponent="valorDescontofixo" 
      :estrelaComponent="estrelaFixa" 
      view="Home"
    />
  </div>
</template>

<script>

import CardProduto from "../components/card/CardProduto.vue"
import axios from 'axios'

export default {
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
      buttonCard: "heart"
    }
  }, methods: {
        getProdutos(){
          
            // axios.get(`https://run.mocky.io/v3/5ab15ba4-fe75-4a4f-b54c-7efa540e3e3d`)
            // axios.get(`https://run.mocky.io/v3/1928107e-7eed-41e6-b662-c4b389c01817`)
            axios.get(`https://run.mocky.io/v3/e1eca572-f05d-40b5-8cbd-4afdc5c7d19c`)
            .then((response)=> {
                console.log(response.data)
                this.produtos = response.data.products
                console.log("data")
                console.log(response.data.products)
                localStorage.setItem("response.data.produtos", JSON.stringify(response.data.products))
            })
            .catch((error) => {
                console.log(error)
            })
        }
    },
    created() {
        this.getProdutos();
        console.log("created")
    }
}
</script>
