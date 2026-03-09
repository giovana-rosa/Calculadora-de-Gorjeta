<script setup>
import EntradaComponent from "../components/entradaComponent.vue";
import SaidaComponent from "../components/saidaComponent.vue";
import { ref } from "vue";

const step = ref(1);

const bill = ref("");
const tip = ref("");
const people = ref("");

const total = ref(0);
const tipValue = ref(0);
const perPerson = ref(0);
const message = ref("");
const calculated = ref(false);


function calculate() {
  const billValue = Number(bill.value);
  const tipPercent = tip.value === "" ? 0 : Number(tip.value); 
  const peopleCount = Number(people.value);

  if (billValue <= 0 || peopleCount <= 0) {
    alert("O valor da conta e o número de pessoas devem ser maiores que 0");
    message.value = "Algo deu errado.";
    calculated.value = false;
    return;
  }

  tipValue.value = (billValue * tipPercent) / 100;
  total.value = billValue + tipValue.value;
  perPerson.value = total.value / peopleCount;
  message.value = "Ok.";
  calculated.value = true;
}
</script>

<template>
  <div class="app">
  <h1 class="title">Calculadora de Gorjeta e Divisão</h1>

  <!-- Parte 1: tela inicial -->
    <div v-if="step === 1" class="page">
      <h2 class="subtitle">Calcule sua gorjeta</h2>
      <button @click="step = 2" class="aqui">AQUI</button>
    </div>

    <!-- Parte 2: tela de cálculo -->
    <div v-if="step === 2" class="page">
      <EntradaComponent
        :bill="bill"
        :tip="tip"
        :people="people"
        @update:bill="bill = $event"
        @update:tip="tip = $event"
        @update:people="people = $event"
        @click="calculate"
      />
      </div>

      <div class="page">
      <SaidaComponent
      v-if="calculated"
        :total="total"
        :tipValue="tipValue"
        :perPerson="perPerson"
        :message="message"
        :calculated="calculated"
      />
      </div>
      
    
  </div>
</template>

<style scoped>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #fafafa;
}

.app {
  max-width: 1000px;
  margin: 0 auto;
  padding: 24px;
}

.title {
  font-size: 1.7rem;
  margin: 2px 0 60px 0;
  text-align: center;
  color: #673ab6;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

.subtitle {
  font-size: 1.3rem;
  margin: 0 0 5px 0;
  padding: 5vw 0 0 0;
  text-align: center;
  color: #673ab6;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
.page {
  display: grid;
  gap: 30px;
  padding-bottom: 30px;
}
.aqui {
  display: block;
  margin: 0 auto;
  padding: 10px 20px;
  font-size: 25px;
  color: #fff;
  background: #673ab6;
  border: none;
  border-radius: 7px;
  cursor: pointer;
}
</style>