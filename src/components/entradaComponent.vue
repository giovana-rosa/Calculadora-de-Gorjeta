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
  background: #e8daff;
  border: 1px solid #ab9ac9;
  border-radius: 7px;
  padding: 12px;
  box-shadow: rgba(17, 17, 26, 0.1) 0px 8px 24px, rgba(17, 17, 26, 0.1) 0px 16px 56px, rgba(17, 17, 26, 0.1) 0px 24px 80px;
}

.panel h2 {
  margin: 0 0 6px 0;
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
  font-size: 14px;
  border: 1px solid #673ab6;
  border-radius: 5px;
  background: #673ab6;
  cursor: pointer;
  color: #fff;
  font-weight: 600;
  display: block;
  margin: 0 auto;
  padding: 4px 6px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
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