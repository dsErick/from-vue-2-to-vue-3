<template>
<div>
    <BaseInput v-model="myInput" />
</div>
</template>

<script>
import { defineAsyncComponent } from 'vue'

export default {
    name: 'App',
    components: {
        BaseInput: defineAsyncComponent(() => import('./components/BaseInput'))
    },
    data() {
        return { myInput: 'asd' }
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
