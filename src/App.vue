<script setup>
import { reactive, computed } from 'vue';

const calculadora = "Calculadora Aritmética";
const digite = "Digite os números desejados nos campos abaixo";

const estado = reactive({
 contador: 0,
 numero1: 0,
 numero2: 0,
 filtro: 'multiplicacao',
 resultado: undefined,
});

function incrementar() {
 estado.contador++;
}

function decrementar() {
 estado.contador--;
}

const multiplicacao = () => {
 return estado.numero1 * estado.numero2;
};

const adicao = () => {
 return estado.numero1 + estado.numero2;
};

const subtracao = () => {
 return estado.numero1 - estado.numero2;
};

const divisao = () => {
 return estado.numero1 / estado.numero2;
};

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
   <input type="number" v-model.number="estado.numero1">
   <input type="number" v-model.number="estado.numero2">
   <select v-model="estado.filtro">
    <option value="multiplicacao">Multiplicação</option>
    <option value="adicao">Adição</option>
    <option value="subtracao">Subtração</option>
    <option value="divisao">Divisão</option>
   </select>
   <button @click="calcular">Calcular</button>
  </div>
 </div>
</template>

<style scoped>

h1 {
  color:blue;
}

h3 {
  color:rgb(69, 69, 204);
}

body{
  background-color:rgb(90, 90, 100); 
}

</style>
