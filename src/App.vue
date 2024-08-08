<script setup>
  import {ref, watch} from 'vue';

  const valor1 = ref (0);
  const valor2 = ref (0);
  const operacao = ref ('');
  const resultado = ref (null);

  function calcular() {
    const num1 = parseFloat(valor1.value);
    const num2 = parseFloat(valor2.value);

  switch (operacao.value) {
    case '+':
        resultado.value = num1 + num2;
      break;
    case '-':
        resultado.value = num1 - num2;
      break;
    case '*':
        resultado.value = num1 * num2;
      break;
      case '/':
        if (num2 === 0) {
          resultado.value = 'Não é possível dividir por zero.';          
        } else {
          resultado.value = num1 / num2;
        }
      break;
    default:
        resultado.value = 'Operação inválida';
      break;
    }
  }

  watch([valor1, valor2, operacao], calcular);
</script>

<template>
  <div class="calculadora">
    <div class="input-container">
      <input type="number" v-model.number="valor1" placeholder="Digite o primeiro valor">
      <select v-model="operacao">
        <option value="">Escolha a operação</option>
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input type="number" v-model.number="valor2" placeholder="Digite o segundo valor">
    </div>
    <div v-if="resultado !== null" class="resultado">
      Resultado: {{ resultado }}
    </div>
  </div>
</template>

<style scoped>
  .calculadora {
      background-color: rgb(219, 215, 215) ;
      max-width: 520px;
      margin: 100px auto;
      padding: 20px;
      border: 1px solid #000;
      border-radius: 5px;
      text-align: center;
    }

    .input-container {
      display: flex;
      justify-content: space-between;
      margin-bottom: 10px;
    }

    input, select {
      width: 30%;
      padding: 5px;
      margin: 0 5px;
    }

    button {
      width: 100%;
      padding: 10px;
      font-size: 18px;
      cursor: pointer;
    }

    .resultado {
      margin-top: 10px;
      font-size: 18px;
      font-weight: bold;
    }
</style>