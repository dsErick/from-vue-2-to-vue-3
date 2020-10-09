<template>
<div id="app">
    <salutation-name
        v-model:salutation.capitalize="form.salutation"
        v-model:name.capitalize.reverse="form.name"
    />

    <pre>{{ form }}</pre>
</div>
</template>

<script>
import { reactive, defineAsyncComponent } from 'vue'

export default {
    name: 'App',
    components: {
        SalutationName: defineAsyncComponent(() => import('./components/SalutationName'))
    },
    setup() {
        const form = reactive({
            salutation: 'Mr.',
            name: ''
        })

        return {
            form
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
