<script setup lang="ts">
import { ref } from 'vue'

const dc = ref(0)
const ds = ref(0)
const tp = ref(0)
const res = ref<string>('')

function som() {
  const dcVal = Number(dc.value)
  const dsVal = Number(ds.value)
  const tpVal = Number(tp.value)

  if (
    dcVal < 0 || dcVal > 20 ||
    dsVal < 0 || dsVal > 20 ||
    tpVal < 0 || tpVal > 20
  ) {
    alert("Les notes doivent être entre 0 et 20")
    return
  }

  const moyenne = ((dsVal * 2) + dcVal + tpVal) / 4
  res.value = moyenne.toFixed(2)
}
</script>

<template>
  <div>
    <label for="dc">DC</label>
    <input type="number" id="dc" v-model="dc" />

    <label for="ds">DS</label>
    <input type="number" id="ds" v-model="ds" />

    <label for="tp">TP</label>
    <input type="number" id="tp" v-model="tp" />
  </div>

  <div>
    <input type="button" value="Calculer" @click="som" />
  </div>

  <div>
    <label for="res">Résultat</label>
    <input type="text" id="res" readonly v-model="res" />
  </div>
</template>

<style scoped>
div {
  margin: 10px 0;
}
label {
  margin-right: 5px;
}
input {
  margin-right: 15px;
}
</style>
