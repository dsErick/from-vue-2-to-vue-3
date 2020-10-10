<template>
<div id="app">
    <base-input
        v-model="email"
        @blur="email = 'blurrr@its.cold'"
        label="Email"
        class="bg-red"
        type="email"
    />

    <pre>Email: {{ email }}</pre>

    <!-- <salutation-name
        v-model:salutation.capitalize="form.salutation"
        v-model:name.capitalize.reverse="form.name"
    />

    <pre>{{ form }}</pre> -->
</div>
</template>

<script>
import { ref, reactive, defineAsyncComponent } from 'vue'

export default {
    name: 'App',
    components: {
        BaseInput: defineAsyncComponent(() => import('./components/BaseInput')),
        // SalutationName: defineAsyncComponent(() => import('./components/SalutationName'))
    },
    setup() {
        const form = reactive({
            salutation: 'Mr.',
            name: ''
        })
        const email = ref('')

        return {
            form,
            email
        }
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
