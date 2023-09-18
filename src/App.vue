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
  <div class="container rounded-3">
    <header class="p-5 mb-4 mt-4 bg-dark rounded-3">
      <h1>Calculadora Aritimética</h1>
    </header>
    
    <form>
      <div class="row">
        <div class="col-md-3">
          <input v-model="estado.numero1" @input="calcularResultado" class="form-control mb-3" type="number" placeholder="Primeiro Número">
          <input v-model="estado.numero2" @input="calcularResultado" class="form-control" type="number" placeholder="Segundo Número">
        </div>
        <div class="col-md-1">
          <select v-model="estado.filtro" @change="calcularResultado" class="form-control">
            <option value="soma">soma</option>
            <option value="subtracao">subtração</option>
            <option value="multiplicacao">multiplicação</option>
            <option value="divisao">divisão</option>
          </select>
        </div>
      </div>
        <div class="mt-3">
          <p class="bg-dark rounded-3">Resultado: {{ estado.resultado }}</p>
        </div>
    </form>
  </div>
</template>

<style scoped>
  .container {
    max-width: 500px;
    width: 500px;
    background-color: rgb(185, 171, 209);
    padding: 8px;
    margin-top: 200px
  }

  input {
    max-width: 200px;
    width: 200px;
  }

  header h1 {
    text-align: center;
    font-size: 42px;
    font-weight: bold;
    color: aliceblue;
  }

  select {
    max-width: 200px;
    width: 200px;
    margin-left: 155px;
  }

  p {
    color: aliceblue;
    font-size: 24px;
    padding: 8px;
    font-weight: bold;
  }


</style>
