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

.result {
  font-size: 15px;
  color: #000000;
  margin: 0 0 6px 0;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-weight: 600;
}
</style>
