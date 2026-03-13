<script setup>
const props = defineProps({
  total: Number,
  tipValue: Number,
  perPerson: Number,
  calculated: Boolean,
});
</script>

<template>
  <div class="panel">
    <h2>RESULTADO</h2>

    <div class="result">Total: R${{ total?.toFixed(2).replace(".", ",") }}</div>

    <div class="result">
      Gorjeta:
      <span v-if="calculated && tipValue === 0">Sem gorjeta</span>
      <span v-else-if="calculated">R${{ tipValue?.toFixed(2).replace(".", ",") }}</span>
      <span v-else>0,00</span>
    </div>

    <div class="result">
      Por pessoa: R${{ perPerson?.toFixed(2).replace(".", ",") }}
    </div>
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
  margin: 0 0 6px 0;
  font-size: 16px;
  color: #673ab6;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

.result {
  font-size: 15px;
  color: #000000;
  margin: 0 0 6px 0;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-weight: 600;
}
</style>
