<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    filtro: 'soma',
    numero1: 0,
    numero2: 0,
    resultado: 0
  })

  const operacao = ()=> {
    const { filtro, numero1, numero2 } = estado;

    switch(filtro){
      case 'soma':
        return numero1 + numero2;
      case 'subtracao':
        return numero1 - numero2;
      case 'multiplicacao':
        return numero1 * numero2;
      case 'divisao':
        return numero1 / numero2;
    }

  }

  function calcularResultado(evento) {
  estado.resultado = operacao();
  }

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Calculadora Aritimética</h1>
    </header>
    
    <form>
      <div class="row">
        <div class="col-md-3">
          <input v-model="estado.numero1" @input="calcularResultado" class="form-control mb-3" type="number" placeholder="Primeiro Número">
          <input v-model="estado.numero2" @input="calcularResultado" class="form-control" type="number" placeholder="Segundo Número">
        </div>
        <div class="col-md-2">
          <select v-model="estado.filtro" @change="calcularResultado" class="form-control">
            <option value="soma">soma</option>
            <option value="subtracao">subtração</option>
            <option value="multiplicacao">multiplicação</option>
            <option value="divisao">divisão</option>
          </select>
        </div>
      </div>
    </form>

    <div class="mt-3">
      <p>Resultado: {{ estado.resultado }}</p>
    </div>

  </div>
</template>

<style scoped>
</style>
