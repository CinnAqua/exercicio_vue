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
        return parseFloat(numeroA) + parseFloat(numeroB)
    }
  }
</script>

<template>
  <div class="container">
    <Cabecalho/>
    <Calculadora
    :trocar-operacao="evento => estado.operacao = evento.target.value"
    :numero-a="estado.numeroA" :numero-b="estado.numeroB"
    :get-numero-a="evento => estado.numeroA = evento.target.value"
    :get-numero-b="evento => estado.numeroB = evento.target.value"
    :get-resultado="getResultado"
    />
  </div>
</template>