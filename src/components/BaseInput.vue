<template>
<!-- <div :class="$attrs.class"> -->
<div>
    <label>{{ label }}</label><br>
    <input
        v-bind="{
            // ...$attrs,
            type: $attrs.type,
            onBlur: $attrs.onBlur,
            
            onClick: clickEvent,

            // Cleaner to look at and make sure input event is not overwriten
            onInput: e => $emit('update:modelValue', e.target.value)
            // @input=$emit('update:modelValue', $event.target.value)
        }"
        :value="modelValue"
    >
</div>
</template>

<script>
export default {
    name: 'BaseInput',
    inheritAttrs: false,    // The parent div will not contain the attributes passed on parent component
    props: {
        modelValue: {
            type: [String, Number],
            default: ''
        },
        label: {
            type: String,
            default: null
        }
    },
    setup(props, { attrs }) {
        console.log('Props', Object.entries(props)) // modelValue: '', label: 'Email'
        console.log('Attrs', Object.entries(attrs)) // class: 'bg-red', type: 'email', onBlur: f, onUpdate:modelValue: f

        const clickEvent = e => console.log(e)

        return {
            clickEvent
        }
    }
}
</script>

<style scoped>
input {
    background: darkslateblue;
    color: white;
    font-weight: 600;
    padding: 1rem 1.75rem;
    border-style: solid;
}

.bg-red { background-color: red }
</style>