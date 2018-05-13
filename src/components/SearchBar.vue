<template>
    <div>
        <input @input="onInput" name="search" id="search"/>
    </div>
</template>

<script>
    export default {
        name: 'SearchBar',
        methods: {
            onInput(event) {
                this.$emit('termChange', event.target.value);
            }
        }
    };
</script>

<style>

</style>