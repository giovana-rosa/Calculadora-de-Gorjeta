<script setup>

</script>

<template>
  <div class="panel">
    <h2>Entradas</h2>
    <ul>
      <li>
        <p>Valor: R$</p>
        <input v-model="bill" class="input" />
      </li>

      <li>
        <p>Porcentagem:</p>
        <input v-model="tip" class="input" />
      </li>

      <li>
        <p>Pessoas:</p>
        <input v-model="people" class="input" />
      </li>
    </ul>

    <button class="small-btn" @click="calculate">Calcular</button>
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

.input {
  width: 100%;
  padding: 6px;
  font-size: 12px;
  border: 1px solid #999;
  margin-bottom: 6px;
}

.small-btn {
  font-size: 11px;
  padding: 4px 6px;
  border: 1px solid #999;
  background: #eee;
  cursor: pointer;
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