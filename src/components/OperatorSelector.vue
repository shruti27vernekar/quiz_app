<template>
<div>
    <button @click="$emit('changeOperator', '+')">Addition + </button>
        <button @click="$emit('changeOperator','-')">Substraction - </button>
    <button @click="$emit('changeOperator','*')"> Multiplication * </button>
    <button @click="$emit('changeOperator','/')">Division / </button>
</div>
</template>

<script>
export default {

}
</script>

<style>
</style>
