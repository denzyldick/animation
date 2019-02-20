<template>
    <button  :class="fontAwesome"></button>
</template>
<script>
    export default {
        name: "Button",
        props: ["fontAwesome"]
    };
</script>

