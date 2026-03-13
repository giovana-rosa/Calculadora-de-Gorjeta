<script setup>
import { computed } from "vue";

const props = defineProps({
  bill: Number,
  tip: Number,
  people: Number,
});

const emit = defineEmits([
  "click",
  "update:bill",
  "update:tip",
  "update:people",
]);
const bill = computed({
  get: () => props.bill,
  set: (val) => emit("update:bill", val),
});

const tip = computed({
  get: () => props.tip,
  set: (val) => emit("update:tip", val),
});

const people = computed({
  get: () => props.people,
  set: (val) => emit("update:people", val),
});

function handleClick() {
  emit('click');
}
</script>

<template>
  <div class="panel">
    <h2>ENTRADAS</h2>
    <ul>
      <li>
        <p>Valor: R$</p>
        <input v-model.number="bill" class="input" />
      </li>

      <li>
        <p>Porcentagem:</p>
        <input v-model.number="tip" class="input" />
      </li>

      <li>
        <p>Pessoas:</p>
        <input v-model.number="people" class="input" />
      </li>
    </ul>

    <button class="small-btn" @click="handleClick">CALCULAR</button>
  </div>
</template>

<style scoped>
.panel {
  position: relative;
  background: #e8daff;
  border-radius: 7px;
  padding: 20px;
}

.panel::before {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 6px;
  border-radius: 7px 0 0 7px;
  background: linear-gradient(#b377ca, #673ab6);
}

.panel h2 {
  margin: 0 0 10px 0;
  font-size: 16px;
  color: #673ab6;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

.panel p {
  margin: 0 0 6px 0;
  font-size: 15px;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-weight: 600;
}

.input {
  width: 100%;
  padding: 6px;
  font-size: 15px;
  border: 1px solid #673ab6;
  border-radius: 5px;
  margin: 0 0 6px 5px;
  background: #ece1ff;
}

.panel .small-btn {
  font-size: 15px;
  border: none;
  border-radius: 5px;
  background: linear-gradient(90deg, #b377ca, #673ab6);
  cursor: pointer;
  color: #fff;
  font-weight: 600;
  display: block;
  margin: 0 auto;
  padding: 6px 12px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  box-shadow: 0 4px 10px rgba(103, 58, 182, 0.3);
}

.panel ul li{
    display: flex;
}

.panel ul {
  list-style: none;
  padding: 0;
  margin: 0 0 12px 0;
}                   
</style>