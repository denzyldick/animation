<template>
    <div>
        <button v-for="shape in shapes" :key="shape.getName()" @click="$emit('addElement',shape)">
            {{shape.getName()}}
        </button>
    </div>
</template>

<script>
    export default {
        name: "Catalog",
        data: function () {
            return {
                shapes: [{

                    style: {
                        position: 'absolute',
                        marginLeft: null,
                        marginRight: null,
                        marginTop: null,
                        marginBottom: null,
                        border: '2px solid red',
                        width: '200px',
                        height: '200px',
                        top: null,
                        left: null,
                        right: null,
                        background: null
                    },
                    getName: () => 'square#' + Math.random()
                },
                    {
                        style: {
                            position: 'absolute',
                            borderLeft: '50px solid transparent',
                            borderRight: '50px solid transparent',
                            borderBottom: '100px solid red',
                            width: '0px',
                            height: '0px',
                            bottom: null,
                            left: null,
                            right: null,
                            background: null
                        },
                        getName: () => 'square#' + this.elements.length
                    },
                    {
                        style: {
                            background: null,

                            position: 'absolute',
                            border: '2px solid green',
                            width: '200px',
                            height: '200px',
                            bottom: null,
                            left: null,
                            borderRadius: '50%'
                        },
                        getName: () => 'cicle#01'

                    }, {
                        style: {
                            position: 'absolute',
                            width: '200px',
                            height: '200px',
                            bottom: null,
                            left: null,
                            backgroundImage: "url('https://via.placeholder.com/200x200')"
                        },
                        getName: () => 'cicle#01'

                    }]
            }
        }
    }
</script>

<style scoped>

</style>