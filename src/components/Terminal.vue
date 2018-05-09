<template>
    <div class="terminal" ref="terminal">
        <prompt :active="true" ></prompt>
    </div>
</template>

<script>
    import Prompt from './prompt.vue';


    export default {
        name: "Terminal",
        components: {
            Prompt
        },

    }
</script>

<style scoped>

</style>