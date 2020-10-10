<template>
    <label>{{ label }}</label><br>
    <input
        v-bind="{
            ...$attrs,
            // type: $attrs.type,
            
            // onBlur: $attrs.onBlur,
            onBlur: blurEvent,
            onClick: clickEvent,

            // Cleaner to look at and make sure input event is not overwriten
            onInput: e => $emit('update:modelValue', e.target.value)
        }"
        :value="modelValue"
    >
</template>

<script>
export default {
    name: 'BaseInput',
    // inheritAttrs: false,    // The parent div will not contain the attributes passed on parent component
    emits: {
        blur: null,
        'update:modelValue': null
    },
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
    setup(props, { attrs, emit }) {
        console.log('Props', Object.entries(props)) // modelValue: '', label: 'Email'
        console.log('Attrs', Object.entries(attrs)) // class: 'bg-red', type: 'email'

        const clickEvent = e => console.log(e)
        const blurEvent = () => emit('blur')

        return {
            clickEvent,
            blurEvent
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