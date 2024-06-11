<script setup>
    const props = defineProps([
        'trocarOperacao',
        'numeroA',
        'numeroB',
        'getNumeroA',
        'getNumeroB',
        'getResultado',
        ])
</script>

<template>
    <div class="calculadora">
        <input
        @keyup="props.getNumeroA"
        :value="props.numeroA" type="number" placeholder="0"
        >
        <select
        @change="props.trocarOperacao"
        >
            <option value="adicao">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">x</option>
            <option value="divisao">:</option>
        </select>
        <input
        @keyup="props.getNumeroB"
        :value="props.numeroB" type="number" placeholder="0"
        >
        <span>=</span>
        <span class="resultado">
            {{ props.getResultado() }}
        </span>
    </div>
</template>

<style scoped>
    * {
        text-align: center;
    }
    .calculadora {
        margin: 25vh;
    }
    input {
        appearance: textfield;
        width: 10vw;
        height: 10vw;
        font-size: 5vw;
        margin: 0 2vw;
        border-radius: 10px;
    }
    select {
        width: 8vw;
        height: 8vw;
        font-size: 5vw;
        background-color: white;
        border-radius: 10px;
    }
    option {
        font-size: 1vw;
    }
    span {
        display: inline-block;
        font-size: 5vw;
    }
    .resultado {
        margin-left: 2vw;
        width: 10vw;
    }
</style>