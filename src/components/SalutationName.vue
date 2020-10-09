<template>
<div>
    <select @change="$emit('update:salutation', $event.target.value)">
        <option value="">-</option>
        <option
            v-for="item in salutations"
            :key="item"
            :value="item"
            :selected="salutation === item"
        >
            {{ item }}
        </option>
    </select>

    <input
        type="text"
        :value="name"
        @input="$emit('update:name', $event.target.value)"
    >
</div>
</template>

<script>
const salutations = [
    'Mr.', 'Mrs.', 'Miss', 'Mx.', 'Dr.'
]

export default {
    props: {
        salutation: {
            type: String, default: ''
        },
        name: {
            type: String, default: ''
        }
    },
    setup() {
        return {
            salutations
        }
    }
}
</script>

<style scoped>
div {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
}

select, input {
    padding: 1rem;
}

select { margin-right: 0.5rem }

input { width: 50% } 
</style>
