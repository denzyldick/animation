<template>
    <div class="canvas" ref="canvas" @mousemove="pointer">
        <div class="frame" v-if="selectedFrame !== null">
            <div class="elementToAnimate " v-for="element in  selectedFrame.elements"
                 :style="element.style" :key="element.name" @click="moveStarted(element,$event)"
                 @mousemove="moveElement"></div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Canvas",
        props: ['element'],
        data: function () {
            return {
                clientX: null,
                clientY: null,
            }
        },
        methods: {
            pointer: function ($event) {
                // console.info($event)
            },
            moveStarted($event) {

            },

            moveElement: function ($event) {

                this.clientX = $event.clientX;
                this.clientY = $event.clientY;

                if (
                    this.element !== null && $event.clientY >= this.$refs.canvas.getBoundingClientRect().y &&
                    $event.clientY <= this.$refs.canvas.getBoundingClientRect().y + this.$refs.canvas.clientHeight &&
                    $event.clientX >= this.$refs.canvas.getBoundingClientRect().x &&
                    $event.clientX <= this.$refs.canvas.getBoundingClientRect().x + this.$refs.canvas.clientWidth
                ) {

                    // console.log(this.$refs.canvas.clientWidth, 'canvas width') console.log(this.$refs.canvas.clientHeight, 'canvas height') console.log(this.$refs.canvas.clientTop, 'canvas top') console.log(this.$refs.canvas.getBoundingClientRect(), 'canvas bounded
                    // client rect')
                    //
                    // console.log($event.clientX, 'ClientX'); console.log($event.clientY, 'ClientY'); console.log(this.element.$el.clientWidth, 'Element width') console.log(this.element.$el.getBoundingClientRect(), 'Element bounded client rect')  if
                    // (this.startedY > $event.clientY) {      newY = ($event.clientY - this.startedY) + this.startedY  } else if (this.startedY < $event.clientY) {      newY = this.startedY - (this.startedY - $event.clientY)  }
                    // this.element.$el.getBoundingClientRect().x = newX

                    if (this.startedX < $event.clientX) {
                        // console.log('right');
                        this.element.style.left = ($event.clientX - this.$refs.canvas.getBoundingClientRect().x) + 'px';

                    } else {
                        this.element.style.left = this.$refs.canvas.getBoundingClientRect().x - ($event.clientX - this.$refs.canvas.getBoundingClientRect().width) + 'px';

                        console.log(this.$refs.canvas.getBoundingClientRect().x, 'canvas')
                        console.log($event.clientX, 'client')
                    }

                    if (this.startedY < $event.clientY) {
                        // console.log('top') this.element.style.top = $event.clientY - this.$refs.canvas.getBoundingClientRect().y + 'px';
                    } else {
                        // console.log('bottom') this.element.style.top = $event.clientY + 'px'
                    }

                    this.startedX = $event.clientX;
                    this.startedY = $event.clientY;
                    // this.element.style.left = ($event.clientX - this.$refs.canvas.getBoundingClientRect().x) + 'px'; this.element.style.top = $event.clientY - this.$refs.canvas.getBoundingClientRect().y + 'px'
                } else {
                    // console.log($event.clientX, this.startedX)
                }
            }

        }
    }
</script>

<style scoped>
    .canvas {
        background-size: 40px 40px;
        background-image: linear-gradient(to right, #ccc 1px, transparent 1px), linear-gradient(to bottom, #ccc 1px, transparent 1px);
        border: 1px solid #000;
        width: 100%;
        height: 100%;
    }
</style>