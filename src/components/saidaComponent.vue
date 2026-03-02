<template>
  <div class="panel">
    <h2>Resultado</h2>
    <div class="result">Total: {{ total }}</div>
    <div class="result">Gorjeta: {{ tipValue }}</div>
    <div class="result">Por pessoa: {{ perPerson }}</div>
    <div class="result">{{ message }}</div>
  </div>
</template>

<style scoped>
.panel {
  background: #fff;
  border: 1px solid #ddd;
  padding: 12px;
}

.panel h2 {
  margin: 0 0 6px 0;
  font-size: 13px;
}

.result {
  font-size: 12px;
  color: #555;
}
</style>