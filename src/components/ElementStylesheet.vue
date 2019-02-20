<template>
    <div class="propeties" v-if="element !==null">
        <div v-for="(value,key) in element.style" :key="key">
            <label>
                {{key}}
                <input type="text" :value="value" v-on:change="changeStyle(key,$event)">
            </label>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ElementStylesheet",
        props: ['element'],
        methods: {
            changeStyle(key, $event) {
                this.element.style[key] = $event.target.value;
                this.$emit('changed', this.element);
            }
        }
    }
</script>

<style scoped>

</style>