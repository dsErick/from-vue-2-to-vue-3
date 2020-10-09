<template>
<input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
>
</template>

<script>
export default {
    name: 'BaseInput',
    props: {
        modelValue: {
            type: [String, Number],
            default: ''
        }
    }
}
</script>

<style>
input {
    background: darkslateblue;
    color: white;
    font-weight: 600;
    padding: 1rem 1.75rem;
    border-style: solid;
}
</style>