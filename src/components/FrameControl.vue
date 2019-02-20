<template>

    <div v-for="frame in frames" :key="frame.name" style="margin-right:3px"
         v-on:click="selectedFrame = frame">
        <img :class="{'selectedFrame':(frame === selectedFrame)}" :src="frame.image" alt=""
             style="height:40px;width:40px;float:left;margin-right:10px;">
    </div>


</template>

<script>
    export default {
        name: "FrameControl",
        props: ['frames'],
        data: function () {
            return {
                selectedFrame: null,
            }
        }
    }
</script>

<style scoped>

</style>