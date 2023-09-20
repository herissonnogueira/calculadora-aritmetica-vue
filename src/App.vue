<script>
export default {
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: '+',
      resultado: 0,
    };
  },
  methods: {
    calcularResultado() {
      const num1 = parseFloat(this.numero1);
      const num2 = parseFloat(this.numero2);

      if (!isNaN(num1) && !isNaN(num2)) {
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
            if (num2 !== 0) {
              this.resultado = num1 / num2;
            } else {
              this.resultado = 'Divisão por zero';
            }
            break;
          default:
            this.resultado = 0;
        }
      } else {
        this.resultado = 0;
      }
    },
  },
};
</script>

<template>
  <div class="calculadora">
    <h1>Calculadora Aritmética</h1>
    <div class="inputs">
      <input v-model="numero1" type="number" placeholder="Número 1" @input="calcularResultado" />
      <select v-model="operacao" @change="calcularResultado">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input v-model="numero2" type="number" placeholder="Número 2" @input="calcularResultado" />
    </div>
    <div class="resultado">
      <h2>Resultado:</h2>
      <p>{{ resultado }}</p>
    </div>
  </div>
</template>

<style scoped>
.calculadora {
  font-family: sans-serif;
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  color: brown;
  background-color: burlywood;
  border-radius: 5px;
  text-align: center;
}

h1 {
  font-size: 24px;
  margin-bottom: 10px;
}

.inputs {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

input[type="number"],
select {
  padding: 10px;
  margin: 5px;
  border: 1px solid brown;
  border-radius: 3px;
}

.resultado {
  font-size: 20px;
  font-weight: bold;
}
</style>
