<script setup>
import { ref } from 'vue'
import ButtonChild from './ButtonChild.vue'
import { formataPreco } from '@/utils/produtoUtils'
const props = defineProps(['nome', 'preco', 'categoria', 'id'])
const novoPreco = ref(props.preco)
defineEmits(['fechar'])
</script>

<template>
    <div class="overlay">
        <div class="produto-dialog">
            <h2>{{ props.nome }}</h2>
            <p>Preço: {{ formataPreco(props.preco) }}</p>
            <p> Categoria: {{ props.categoria }}</p>
            <input type="number" v-model.number="novoPreco">
            <ButtonChild >Corrigir Preço</ButtonChild>
            <ButtonChild @clique="$emit('fechar')">Fechar</ButtonChild>
        </div>
    </div>
</template>

<style scoped>
.produto-dialog{
    border: 1px solid #ccc;
    border-radius: 8px;
    padding: 16px;
    margin-top: 16PX;
    background-color: white;
    min-width: 320px;
}
.overlay{
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
}
</style>