<template>
    <div class="container">

        <Player/>

        <FrameControl/>

        <Catalog/>

    </div>
</template>

<script>
    import Player from "../components/Player";
    import Catalog from "../components/Catalog";
    import FrameControl from "../components/FrameControl";

    export default {
        name: 'Home',
        components: {FrameControl, Catalog, Player},
        props: {
            msg: String
        },
        data: function () {
            return {
                speed: 1,
                startedX: null,
                startedY: null,
                element: null,
                selectedFrame: null,
                elements: [],
                sheet: {
                    width: 1200,
                    height: 800
                },
                frames: [],
                intervalId: null,
                loop: false,
                playing: false
            }
        },
        methods: {

            duplicateFrame: function () {
                this.frames.push(JSON.parse(JSON.stringify(this.selectedFrame)));
            },
            play: function () {
                this.player.playing = true;
                let index = 0;
                let this_ = this;
                this.intervalId = setInterval(function () {
                    console.log(index)
                    if (index < this.frames.length) {

                        this.selectedFrame = this.frames[index];
                        index++;
                    } else {
                        if (this_.loop) {
                            index = 0;
                            this.selectedFrame = this.frames[index];

                        } else {
                            this.stop();
                        }
                    }
                }.bind(this), this.speed)
            },
            stop: function () {
                if (this.intervalId !== null) {
                    this.player.playing = false;
                    clearInterval(this.intervalId);
                    this.intervalId = null
                }
            },
            addFrame() {
                let name = 'frame' + Math.random();
                this.frames.push({image: 'https://via.placeholder.com/200x200', elements: [], name: name})
            },
            moveEnded: function () {
                console.log('ended')
                this.startedX = null;
                this.startedY = null;
                this.element = null;
            },


            addElement: function ($payload) {
                this.selectedFrame.element.push($payload)
            }
        },
        mounted() {
            this.addFrame();
        }
    }
</script>
<style scoped="scoped" lang="scss">
    * {
        margin: 0;
    }
</style>
