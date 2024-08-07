<script setup>
  let valor1 = 0
  let valor2 = 0
  const operacao = ''
  const resultado = 0

  function calcular() {
    const num1 = parseFloat(this.valor1);
    const num2 = parseFloat(this.valor2);
  switch (this.operacao) {
    case '+':
        this.resultado = num1 + num2;
      break;
    case '-':
        this.resultado = num1 - num2;
      break;
    case '*':
        this.resultado = num1 * num2;
      break;
      case '/':
        if (num2 === 0) {
          this.resultado = 'Não é possível dividir por zero.';          
        } else {
        this.resultado = num1 / num2;
        }
      break;
    default:
        this.resultado = 'Operação inválida';
      break;
    }
  };
</script>

<template>
  <div class="calculadora">
    <div class="input-container">
      <input type="number" v-model.number="valor1" placeholder="Digite o primeiro valor">
      <select v-model="operacao">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input type="number" v-model.number="valor2" placeholder="Digite o segundo valor">
    </div>
    <button @click="calcular">Calcular</button>
    <div v-if="resultado !== null" class="resultado">
      Resultado: {{ resultado }}
    </div>
  </div>
</template>

<style scoped>
  .calculadora {
      max-width: 520px;
      margin: 100px auto;
      padding: 20px;
      border: 1px solid #ccc;
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
