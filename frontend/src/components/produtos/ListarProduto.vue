<!-- Teste -->
<template>
    <div class="listagemProdutos">
        <h3>Produtos Cadastrados</h3>
        {{ mensagem }}

        <a href="/produtos/cadastrar">Cadastrar</a>

        <ul class="produtos-lista">
            <li v-for="produto in produtos">
                <img :src="`http://localhost:3000/uploads/${produto.imagem}`"  width="100"/>
                <p>{{ produto.nome }}</p>
                <span class="valor">R$ {{ produto.valor }}</span>
                <a href="#" class="btn-adicionar-produto" @click="adicionarProduto(produto)">
                    Adicionar ao carrinho
                </a>
            </li>
        </ul>
    </div>
</template>

<script>

import axios from 'axios'
import { mapActions } from 'vuex'

const minhaApi = axios.create({
    baseURL: "http://localhost:3000",
    headers: {
        'Content-Type': 'application/json'
    }
})

export default {
    name: "ListarProduto",
    data() {
        return {
            produtos: [],
            mensagem: null
        }
    },
    async mounted() {
        this.listar()
    },
    methods: {
     ...mapActions("carrinho", ["adicionarProduto"]),
    async listar() {
            const responce = await minhaApi.get("/produto/")
            this.produtos = responce.data
        },
    },
    async deletar(id) {
        const responce = await minhaApi.delete(`/produto/${id}`)
        this.mensagem = responce.data
        this.listar()
    }
}

</script>

<style scoped>
ul {
    width: 500px;
}
ul li {
    float: left;
    width: 100px;
    height: 264px;
    margin-bottom: 10px;
    margin-right: 10px;
    list-style: none;
    font-size: 12px;
    position: relative;
}
ul li span.valor{
    background: green;
    color: #ffffff;
    position: absolute;
    top: 0;
    padding: 3px;
    right: 0;
    font-size: 13px;
}

.btn-adicionar-produto {
    background: #000000;
    width: 100px;
    height: 30px;
    text-align: center;
    display: block;
    text-decoration: none;
    border-radius: 7px;
    position: absolute;
    bottom: 0;
    color: #ffffff;
    font-size: 11px;
    padding-top: 5px;
}
</style>