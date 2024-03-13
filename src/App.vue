<script setup>
import { reactive } from 'vue';

const tipoOperacao = reactive({
  numero1: 0,
  numero2: 0,
  operador: 'adicionar',
});

const resultado = () => {
  const { numero1, numero2, operador } = tipoOperacao;
  switch (operador) {
    case 'adicionar':
      return numero1 + numero2;
    case 'subtrair':
      return numero1 - numero2;
    case 'multiplicar':
      return numero1 * numero2;
    case 'dividir':
      return numero2 !== 0 ? numero1 / numero2 : 'Não pode dividir por zero';
    default:
      return 0;
  }
};
</script>

<template>
  <div class="container">
    <header class="text-center p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Calculadora</h1>
      <p>
        Escolha os números e a operação desejada
      </p>
    </header>
    <form class="row gx-3 align-items-center">
      <div class="row">
        <div class="col-md-3">
          <input type="number" class="form-control" v-model="tipoOperacao.numero1" inputmode="numeric">
        </div>
        <div class="col-md-1">
          <select class="form-control" v-model="tipoOperacao.operador">
            <option value="adicionar">+</option>
            <option value="subtrair">-</option>
            <option value="multiplicar">*</option>
            <option value="dividir">/</option>
          </select>
        </div>
        <div class="col-md-3">
          <input type="number" class="form-control" v-model="tipoOperacao.numero2" inputmode="numeric">
        </div>
        <div class="col-md-5">
          <div class="input-group">
            <span class="input-group-text">Resultado:</span><br>
            <input type="text" class="form-control" :value="resultado()" readonly>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>
input,
select {
  margin: 5px;
  padding: 5px;
  width: 100%;
}

select {
  text-align: center;
}
</style>