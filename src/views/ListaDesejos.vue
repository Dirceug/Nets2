<template>
    <div class="dash">
        <CardProduto 
            :produtosArray="listaDesejos"
            :valorRealComponent="valorRealfixo" 
            :valorDescontoComponent="valorDescontofixo" 
            :estrelaComponent="estrelaFixa" 
            view="Desejos"
        />        
  </div>

</template>

<script>
import CardProduto from "../components/card/CardProduto.vue"
// const listaDesejos = JSON.stringify(localStorage.produtos) || []
export default {
    components: {
        CardProduto
    }
    ,data() {
        return {
        produtos: [],
        estrelaFixa: 5,
        valorRealfixo: "123,99",
        valorDescontofixo:"99,99",
        listaDesejos: {},
        listaDesejosArray: [],
        buttonCard: "cancel"
        }
    }
    ,created() {
        console.log("created")
        this.getListaDesejos()
        //verifica se a lista de desejeos existe lo localStorage
        const listaDesejosString = localStorage.getItem("listaDesejos");
        if (listaDesejosString) {
            // Converte a lista de desejos de string para objeto JavaScript
            this.listaDesejos = JSON.parse(listaDesejosString);
        }   
        this.produtosArray = this.listaDesejos;
    }
    ,methods: {
        goToWhishList(produto) {
            console.log("Inserir na lista de desejos");
            // console.log(produto.selectedProduct);
            const novoProduto = {
                selectedProduct: produto.selectedProduct,
                name: produto.name,
                valorRealfixo: "123,99",
                valorDescontofixo: "99,99",
                estrelaFixa: 5,
            };
        console.log(novoProduto);
        // Adiciona o novo produto à lista
        this.listaDesejos[novoProduto.selectedProduct] = {...this.listaDesejos, [novoProduto.selectedProduct]: novoProduto};
        // Salva a lista de desejos no localStorage
        localStorage.setItem("listaDesejos", JSON.stringify(this.listaDesejos));
        }
        ,getListaDesejos(){
            console.log("getListaDesejos no methods")
            this.listaDesejosArray = Array.from(this.listaDesejos);
        },
        watch: {
            listaDesejos() {
                console.log("watch")
                this.produtosArray = this.getListaDesejos();
                console.log("ListaDesejos")
                console.log(this.produtos)
                // setTimeout(()=> {
                //     this.$forceUpdate();
                // }, 0)
                this.$forceUpdate();
            },
        }
    }
    ,mounted() {
        //this.getListaDesejos();
        console.log("abrir lista de desejos")
        console.log(JSON.stringify(this.listaDesejos.product.selectedProduct))
        // console.log(listaDesejos)
        this.listaDesejos = this.getListaDesejos();
        console.log("Lista de desejos aberta no mounted")
    }
    ,computed: {
    produtosArray() {
        return this.listaDesejos.map(produto => {
            return produto;
        });
    }
}



}
</script>

<style scoped>
    #dash{
        max-width: 100%;
        display: flex;
        flex-wrap: wrap;
    }
</style>