<template>
    <div>
        <label>
            Play speed
            <input type="range" v-model="speed">
        </label>
        <button v-for="control in controls" @click="emit(control.key)" :key="control.key">{{control.key}}</button>
    </div>
</template>

<script>
    export default {
        name: "Player",
        data: function () {
            return {
                speed: 0,
                controls: [
                    {key: 'play'},
                    {key: 'stop'},
                    {key: 'stop'},
                    {key: 'undo'},
                    {key: 'redo'},
                    {key: 'add_frame'},
                    {key: 'duplicate_frame'}
                ]
            }
        },
        methods: {
            emit: function ($event) {
                this.$emit($event)
            }
        }
    }
</script>

<style scoped>

</style>