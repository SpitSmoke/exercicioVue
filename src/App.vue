<template>
  <div class="calculadora">
    <h1>
      <span class="batman-bat">BAT</span><span class="batman-s">-</span
      ><span class="batman-man">CALCULO</span>
    </h1>

    <div class="inputs">
      <input v-model.number="num1" type="number" placeholder="Insira o primeiro número" />
      <input v-model.number="num2" type="number" placeholder="Insira o segundo número" />
    </div>

    <div class="select-operacao">
      <select v-model="operacao">
        <option value="soma">Soma (+)</option>
        <option value="subtracao">Subtração (-)</option>
        <option value="multiplicacao">Multiplicação (*)</option>
        <option value="divisao">Divisão (/)</option>
      </select>
    </div>

    <div class="resultado">
      <h2>Resultado: {{ resultado }}</h2>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const num1 = ref(0)
const num2 = ref(0)
const operacao = ref('soma')

const resultado = computed(() => {
  switch (operacao.value) {
    case 'soma':
      return num1.value + num2.value
    case 'subtracao':
      return num1.value - num2.value
    case 'multiplicacao':
      return num1.value * num2.value
    case 'divisao':
      return num2.value !== 0 ? num1.value / num2.value : 'Erro (divisão por 0)'
    default:
      return 0
  }
})
</script>

<style scoped>
@font-face {
  font-family: 'MinhaFonte';
  src: url('../../vue-project/batman_forever/batmfa__.ttf') format('truetype');
}

body {
  font-family: 'MinhaFonte', sans-serif;
}

.calculadora {
  min-height: 100vh;
  width: 100vw;
  text-align: center;
  margin-top: 50px;
  background-image: url(https://cdn.ome.lt/legacy/images/galerias/Batman-em-20-momentos/Batman-por-Marshall-Rogers.jpg);
  background-size: cover;
  background-repeat: no-repeat;
  overflow-x: hidden;
}

.inputs {
  margin-bottom: 20px;
  overflow-x: hidden;
}

input {
  padding: 10px;
  margin-right: 10px;
  font-size: 16px;
  width: 200px;
}

select {
  padding: 10px;
  font-size: 16px;
}

.resultado h2 {
  color: #f8f8f8;
}

.batman-bat {
  font-size: 30px;
  margin-bottom: 20px;
  color: #e6f10c;
}

.batman-s {
  font-size: 30px;
  color: #03084e;
}

.batman-man {
  font-size: 30px;
  color: #e6f10c;
}
</style>
