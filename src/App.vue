<script setup>
import EntradaComponent from './components/entradaComponent.vue';
import SaidaComponent from './components/saidaComponent.vue';
import { ref } from 'vue';

const bill = ref('');
const tip = ref('');
const people = ref('');

const total = ref(0);
const tipValue = ref(0);
const perPerson = ref(0);
const message = ref('');

function calculate() {
    const billValue = Number(bill.value);
    const tipPercent = Number(tip.value);
    const peopleCount = Number(people.value);

    if (!billValue || !tipPercent || !peopleCount) {
        alert('Preencha os dados');
        message.value = 'Algo deu errado.';
        return;
    }

    tipValue.value = (billValue * tipPercent) / 100;
    total.value = billValue + tipValue.value;
    perPerson.value = total.value / peopleCount;
    message.value = 'Ok';
}
</script>

<template>
    <div class="app">
        <h1 class="title">Calculadora de Gorjeta e Divisão</h1>

        <div class="layout">
            <EntradaComponent/>                  

            <SaidaComponent/>
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
  font-size: 18px;
  margin: 0 0 12px 0;
}

.layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 18px;
}
</style>