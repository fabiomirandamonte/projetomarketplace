<template>
    <div class="container2">
        <h3>Resumo da Compra</h3>
    
        <DadosDoComprador />

        <h4>Escolha a forma de pagamento </h4>

        <input type="radio" v-model="formaDePagamento" name="formaDePagamento" v-on:change="alterarFormaDePagamento" value="cc"/> Cartão
        <input type="radio" v-model="formaDePagamento" name="formaDePagamento" v-on:change="alterarFormaDePagamento" value="pix"/> PIX
        <input type="radio" v-model="formaDePagamento" name="formaDePagamento" v-on:change="alterarFormaDePagamento" value="boleto"/> Boleto
        <br>
        <img :src="qrCodeGerado" v-show="formaDePagamento == 'pix'" />

        <div v-show="formaDePagamento == 'cc'">
            <br>
            Titular<br>
            <input type="text" name="cc_titular"><br>
            Número<br>
            <input type="text" name="cc_numero"><br>
            CVV<br>
            <input type="text" name="cc_cvv"><br>
            Validade<br>  
            <input type="text" name="cc_validade"><br>
        </div>

        <Cupom />

        <h2>Valor sem desconto R$ {{ valores.valorSemDesconto }}</h2>
        <h2>Desconto R$ {{ valores.desconto }}</h2>
        <h2>Total R$ {{ total }}</h2>
    </div>

</template>

<script>
import { mapGetters } from 'vuex';
import QRCode from 'qrcode';
import Cupom from './Cupom.vue';
import minhaApi from '../clientes/EditarCliente.vue';
import DadosDoComprador from '../carrinhos/DadosDoComprador.vue'

export default {
    name: "Checkout",
    computed: {
    },
    components: {
        Cupom,
        DadosDoComprador
    },
    data(){
        return {
            formaDePagamento: null,
            qrCodeGerado: null
        }
    },
    computed: {
        ...mapGetters("carrinho", ["cliente_id", "valores","total"]),
    },
    methods: {
        alterarFormaDePagamento() {
            if (this.formaDePagamento == 'pix') {
                this.gerarPix()
            } else if(this.formaDePagamento == 'cc'){
                console.log('exibir formulario pedindo dados do CC');
            } else {
                console.log('gerar boleto em PDF');
            }
        },
        gerarPix() {
            QRCode.toDataURL(`${this.total};${this.cliente_id}`, {
                width: 300,
                height: 300,
                margin: 1
            }, async (err, url) => {
                this.qrCodeGerado = await url
            })
        },


        async mounted() {
            try {
                const response = await minhaApi.get(`/cliente/${this.id}`);
                this.nome = response.data.nome;
                this.endereco = response.data.endereco;
            } catch (error) {
                console.error('Erro ao obter os dados do comprador', error);
            }
        }
       
    }
}

</script>

<style scoped>
.container2 {
    display: flex;
    flex-direction: column;
    gap: 5px;
    width: 541px;
    padding: 35px;
}
</style>