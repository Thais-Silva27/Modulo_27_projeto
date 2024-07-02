<script setup>    
    const calculadora = "Calculadora Aritmética";
    const digite = "Digite os números desejados nos campos abaixo";
  
    const estado = reactive({
      contador: 0,
      numero1: 0,
      numero2: 0,
      filtro: 'multiplicacao', 
    });
  
    function incrementar() {
      estado.contador++;
    }
  
    function decrementar() {
      estado.contador--;
    }
  
    function calcular() {
      switch (estado.filtro) {
        case "multiplicacao":
          estado.resultado = multiplicacao();
          break;
        case "adicao":
          estado.resultado = adicao();
          break;
        case "subtracao":
          estado.resultado = subtracao();
          break;
        case "divisao":
          estado.resultado = divisao();
          break;
      }
    }
  
    const multiplicacao = () => {
      return estado.numero1 * estado.numero2;
    };
  
    const adicao = () => {
      return Number(estado.numero1 + estado.numero2);
    };
  
    const subtracao = () => {
      return estado.numero1 - estado.numero2;
    };
  
    const divisao = () => {
      return estado.numero1 / estado.numero2;
    };
  
  
    const mostrarResultado = computed(() => {
      return estado.resultado !== undefined;
    });
  
  
    const resultado = computed(() => {
      return estado.resultado;
    });
  
  </script>


<template>
    <div>
      <h1>{{ calculadora }}</h1>
      <h3>{{ digite }}</h3>
      <hr>
  
      <p>{{ estado.contador }}</p>
      
      <div v-if="mostrarResultado">
        <p>Resultado: {{ resultado }}</p>
      </div>
  
      <div>
        <input type="number" v-model.number="numero1">
        <input type="number" v-model.number="numero2">
        <select v-model="filtro">
          <option value="multiplicacao">Multiplicação</option>
          <option value="adicao">Adição</option>
          <option value="subtracao">Subtração</option>
          <option value="divisao">Divisão</option>
        </select>
       
      </div>
    </div>
  </template>
   
  
  <style scoped>
  
  </style>
  
