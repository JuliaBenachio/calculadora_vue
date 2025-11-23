<script setup>
import { ref, computed } from "vue";

const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref("soma");

const resultado = computed(() => {
    switch (operacao.value) {
        case "soma":
            return numero1.value + numero2.value;
        case "sub":
            return numero1.value - numero2.value;
        case "mult":
            return numero1.value * numero2.value;
        case "div":
            return numero2.value !== 0
                ? (numero1.value / numero2.value).toFixed(2)
                : "Erro";
        default:
            return 0;
    }
});
</script>

<template>
    <div class="container">
        <h2>Calculadora Aritmética</h2>

        <input type="number" v-model.number="numero1" placeholder="Digite o primeiro número" />

        <input type="number" v-model.number="numero2" placeholder="Digite o segundo número" />

        <select v-model="operacao">
            <option value="soma">Somar</option>
            <option value="sub">Subtrair</option>
            <option value="mult">Multiplicar</option>
            <option value="div">Dividir</option>
        </select>

        <div class="resultado">
            Resultado: {{ resultado }}
        </div>
    </div>
</template>

<style scoped>
.container {
    max-width: 300px;
    margin: 40px auto;
    padding: 20px;
    background: white;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    font-family: Arial, sans-serif;
}

input,
select {
    width: 100%;
    padding: 8px;
    margin: 10px 0;
}

.resultado {
    margin-top: 20px;
    padding: 10px;
    background: #eee;
    border-radius: 5px;
    font-weight: bold;
    text-align: center;
    font-size: 1.2rem;
}
</style>
