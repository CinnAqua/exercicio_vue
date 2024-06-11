<script setup>
  import Cabecalho from '@/components/Cabecalho.vue'
  import Calculadora from '@/components/Calculadora.vue'
  import {reactive} from 'vue'

  const estado = reactive({
    numeroA: 0,
    numeroB: 0,
    resultado: 0,
    operacao: 'adicao',
  })

  const getResultado = () => {
    const {numeroA, numeroB, operacao} = estado
    switch(operacao) {
      case 'subtracao':
        return numeroA - numeroB
      case 'multiplicacao':
        return numeroA * numeroB
      case 'divisao':
        return numeroA / numeroB
      default:
        return numeroA + numeroB
    }
  }
</script>

<template>
  <Cabecalho/>
  <Calculadora/>
  <div class="container">
    <input
    @keyup="evento => estado.numeroA = evento.target.value"
    :value="estado.numeroA" type="number" placeholder="0"
    >
    <select
    @change="evento => estado.operacao = evento.target.value"
    >
      <option value="adicao">+</option>
      <option value="subtracao">-</option>
      <option value="multiplicacao">x</option>
      <option value="divisao">:</option>
    </select>
    <input
    @keyup="evento => estado.numeroB = evento.target.value"
    :value="estado.numeroB" type="number" placeholder="0"
    >
    = {{ getResultado() }}
  </div>
</template>

<style scoped>
  input[type=number] {
    appearance: textfield;
  }
</style>
