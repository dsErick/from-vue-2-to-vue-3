<template>
<div>
    <select @change="updateSalutation">
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
        @input="updateName"
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
        salutationModifiers: {
            default: () => ({})
        },
        name: {
            type: String, default: ''
        },
        nameModifiers: {
            default: () => ({})
        }
    },
    setup(props, { emit }) {
        const updateSalutation = e => {
            let val = e.target.value

            if (props.salutationModifiers.capitalize) val = val.toUpperCase()
            
            emit('update:salutation', val)
        }

        const updateName = e => {
            let val = e.target.value

            if (props.nameModifiers.capitalize) {
                val = val.charAt(0).toUpperCase() + val.slice(1)
            }

            if (props.nameModifiers.reverse) {
                val = val.split('').reverse().join('')
            }

            emit('update:name', val)
        }
        
        return {
            salutations,
            updateSalutation,
            updateName
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
