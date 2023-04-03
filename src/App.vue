<script setup>
import { reactive } from 'vue';
const estado = reactive({
  valor1: 0,
  valor2: 0,
  metodo: 'soma',
})

const operacao = () => {
  const {valor1, valor2, metodo} = estado
  switch(metodo) {
    case 'soma':
      return parseFloat(valor1) + parseFloat(valor2)
    case 'subt':
      return parseFloat(valor1) - parseFloat(valor2)
    case 'mult':
      return parseFloat(valor1) * parseFloat(valor2)
    case 'divi':
      return parseFloat(valor1) / parseFloat(valor2)
    }
}
</script>

<template>
  <div class="container">
    <div class="div-cc">
      <h1>Calculadora Aritmética</h1>
      <input @keyup="evento => estado.valor1 = evento.target.value" type="number" required><br>
      <select @change="evento => estado.metodo = evento.target.value" required>
        <option value="soma">+</option>
        <option value="subt">-</option>
        <option value="mult">*</option>
        <option value="divi">/</option>
      </select><br>
      <input @keyup="evento => estado.valor2 = evento.target.value" type="number" required><br>
      Resultado:
      <h3 class="result"> {{ operacao() }}</h3>
    </div>
  </div>
  {{ estado.filtro }}
</template>

<style scoped>
.container{
  max-width: 1024px;
  width: 100%;
  margin: 0 auto;
  padding: 24px;
  display: flex;
  justify-content: center;
  background-color: #000;
  border: 4px solid #000;
  border-radius: 8px
}
.div-cc{
  max-width: 720px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #ac0184;
  border: 4px solid #fff;
  border-radius: 8px;
  padding: 32px;
  text-align: center;
}

h1{
  color: #fff;
}

input{
  padding: 16px;
  width: 40%;
  font-size: 16px;
}

select{
  padding: 8px;
  font-size: 16px;
}

.result{
  background-color: #eee;
  border-radius: 4px;
  font-size: 32px;
  padding: 8px 16px;
}
</style>
