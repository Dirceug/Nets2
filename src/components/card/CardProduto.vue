<template>
    <div id="produtos">
        <ButtonCard :heart="heart" :cancel="cancel"/>
        <div id="card-produtos" v-for="produto in produtosArray" :key="produto.selectedProduct">
            <img :src="produto.product.image" alt="" class="imagem-produto">
            <a href="#" @click="goToWhishList(produto)">
                <img :src="coracao" :alt="app_name" class="heart" v-if="view==='Home'">
            </a>
            <a href="#" @click="deleteFromWhishList(produto)">
                <img :src="cancelar" :alt="app_name" class="cancel" v-if="view==='Desejos'">
            </a>
            <h3 class="titulo-produto">{{ produto.name }}</h3>
            <p id="estrelas-iteradas2">
                <ul id="estrelas-iteradas">
                    <li v-bind:key="i" v-for="i in Array(estrelaFixa)">
                        <img :src="star" :alt="app_name" class="star">
                    </li >{{ estrelaFixa }}.0
                </ul>
            </p>
            <p class="valor-original">R$ {{ valorRealfixo }}</p>
            <p class="valor-venda">R$ {{ valorDescontofixo }}</p>
            <p>{{ imagem }}</p>
        </div>
    </div>
</template>

<script>
import ButtonCard from "../buttonCard/ButtonCard.vue"
import { useRouter } from 'vue-router';


export default {
    data() {
        return {
            produtos: [],
            coracao: "../../../images/heart-regular.svg",
            cancelar: "../../../images/x-solid.svg",
            estrelaFixa: 5,
            star: "../../../images/star-solid.svg",
            valorRealfixo: "123",
            valorDescontofixo:"99,99",
            listaDesejos: [],
            produtosArray2: [],
            buttonCard: {
                heart: "heart",
                cancel: "cancel"
            },
        }
    },
    created(){
        const listaDesejosString = localStorage.getItem("listaDesejos");
        this.listaDesejos = listaDesejosString ? JSON.parse(listaDesejosString) : [];
        // this.produtosArray2 = this.listaDesejos;
    }
    ,methods:{
        goToWhishList(produto){
            console.log("Inserir na lista de desejos")
            console.log(produto.selectedProduct)
            const produtoDesejado = {
                    selectedProduct: produto.selectedProduct,
                    name: produto.name,
                    valorRealfixo: "123,99",
                    valorDescontofixo: "99,99",
                    estrelaFixa: "5",
                    product: {
                        image: produto.product.image,
                        details: {
                            name: produto.product.details.name
                        },
                        selectedProduct: produto.selectedProduct,
                    }
            }
            console.log(produtoDesejado)
            this.listaDesejos.push(produtoDesejado)
            localStorage.setItem("listaDesejos", JSON.stringify(this.listaDesejos)) 
            // console.log(novoProduto)
        },
        deleteFromWhishList(produto){
            const index = this.listaDesejos.findIndex(item => item.selectedProduct === produto.selectedProduct);
            if (index !== -1) {
                this.listaDesejos.splice(index, 1);
                localStorage.setItem("listaDesejos", JSON.stringify(this.listaDesejos));
                alert("Produto " + produto.name + " excluído com sucesso")
            }
            const router = useRouter();
            router.go({ name: "Desejos"})
            console.log("Produto deletado")
        }, computed: {
            produstosArray(){
                return Array.from(this.listaDesejos);
            }
        }
    }   
    ,components: {

    }, props: {
        produtosArray: Array,
        valorRealComponent: String,
        valorDescontoComponent: String,
        estrelaComponent: String,
        view: String
    },
    imports: {
        ButtonCard
    }
}
</script>

<style scoped>

    #produtos {
        display: flex;
        padding: 5px;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
    }

    #heart {
        border: 2px solid black;
    }

    #cancel {
        border: 2px solid red;
    }

    #card-produtos {
        display: flex;
        flex-direction: column;
        text-align: left;
        width: 150px;
        height: 265px;
        padding: 5px;
        box-shadow: 3px 3px 8px #999;
        position: relative;
        border-radius: 5px;
        margin: 15px;
    }

    #card-produtos:hover {
        box-shadow: 3px 3px 8px #555;
    }

    .imagem-produto{
        width: 150px;
        height: 150px;
    }

    .heart {
        width: 15px;
        height: 15px;
        background-color: #999;
        border-radius: 50px;
        padding: 5px;
        margin: auto;
        margin-left: 0;
        margin-top: 0;
        position: absolute;
        top: 5px;
        right: 5px;
    }    
    
    .heart:hover {
        background-color: red;
        cursor: pointer;
    }

    .cancel {
        width: 15px;
        height: 15px;
        background-color: transparent;
        border-radius: 50px;
        padding: 5px;
        margin: auto;
        margin-left: 0;
        margin-top: 0;
        position: absolute;
        top: 5px;
        right: 5px;
    }    
    
    .cancel:hover {
        background-color: red;
        cursor: pointer;
    }

    .titulo-produto {
        font-size: 12px;
        margin: -10px;
        margin-left: 0;
        position: absolute;
        left: 5px;
        top: 170px;
        width: 160px;
    }

    #estrelas-iteradas {
        display: flex;
        flex-direction: row;
        align-content: flex-start;
        list-style-type: none;
        margin: auto 0;
        position: absolute;
        left: -40px;
        font-size: 14px;
    }

    .star {
        margin: 3px;
    }

    #estrelas-iteradas2 {
        align-content: flex-start;
        justify-content: flex-start;
        position: absolute;
        bottom: 55px;
        left: 1px;
    }

    .valor-original {
        color: #aaa;
        font-size: 14px;
        text-decoration: line-through;
        /* border: 2px solid green; */
        position: absolute;
        bottom: 15px;
        left: 5px;
    }
    
    .valor-venda {
        color: #5a2d82;
        font-size: 18px;
        font-weight: bold;
        /* border: 2px solid purple; */
        margin: 0px;
        margin-left: 0;
        position: absolute;
        bottom: 5px;
        left: 5px;
    }
</style>