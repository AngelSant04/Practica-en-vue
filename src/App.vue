<script setup>
import {ref, computed} from 'vue'

const name = 'Vue JS';
let counter = ref(0);
let arrayNumber = ref([]);

const classCounter = computed(() => {
  if (counter.value > 0) {
    return 'verde';
  }
  if (counter.value < 0) {
    return 'rojo';
  }
  if (counter.value == 0) {
    return 'blanco';
  }
})

const disabledBoton = computed(() => {
  const number = arrayNumber.value.find((num) => num === counter.value);
  return number || number === 0;
})

const aumentar = () => {
  counter.value++;
}

const disminuir = () => {
  counter.value--;
}

const reset = () => {
  counter.value = 0;
}

const agregar = () => {
  arrayNumber.value.push(counter.value);
}
 

</script>

<template>
  <div class="container text-center mt-3">
    <h1> HOLA {{ name.toUpperCase() }}</h1>
    <h2 :class="classCounter"> {{ counter }} </h2>
    <div class="btn-group">
      <button @click="aumentar" class="btn btn-success">Aumentar</button>
      <button @click="disminuir" class="btn btn-danger">Disminuir</button>
      <button @click="reset" class="btn btn-secondary">Resetear</button>
      <button :disabled="disabledBoton" @click="agregar" class="btn btn-primary">Agregar</button>
    </div>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="(numero,index) in arrayNumber" :key="index">{{numero}}</li>
    </ul>
  </div>
</template>

<style>
h1{
  color:Red;
}
.verde{
  color:green
}
.rojo{
  color:red
}
.blanco{
  color:white
}
</style>