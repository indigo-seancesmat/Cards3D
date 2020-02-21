<template>
    <div class="tippy-card"
        @mousemove="handleMouseMove"
        @mouseenter="handleMouseEnter"
        @mouseleave="handleMouseLeave"
        ref="card">
        <div class="tippy-card__inner"
            :style="cardStyle">
            <div class="tippy-card__bg">
                <Still3d v-if="!xymove"
                    :bg-image="bgImage"
                    :depth-map="depthMap"
                    :x="mouseX"
                    :y="mouseY"
                    :sensitivity="sensitivity" />
                <Still3dXYMove v-if="xymove"
                    :bg-image="bgImage"
                    :depth-map="depthMap"
                    :x="mouseX"
                    :y="mouseY"
                    :sensitivity="sensitivity" />
            </div>
            <div class="tippy-card__info">
                <slot name="header"></slot>
                <slot name="content"></slot>
            </div>
        </div>
    </div>
</template>

<script>
import Still3d from "@/components/Still3d";
import Still3dXYMove from "@/components/Still3dXYMove";

export default {
    name: "tippy-card",
    components: {
        Still3d,
        Still3dXYMove
    },
    props: {
        bgImage: {
            type: String,
            required: true
        },
        depthMap: {
            default: String,
            required: true
        },
        sensitivity: Number,
        xymove: {
            type: Boolean,
            default: false
        }
    },
    data: () => ({
        width: 0,
        height: 0,
        mouseX: 0,
        mouseY: 0,
        mouseXEnter: 0,
        mouseYEnter: 0,
        mouseLeaveDelay: null
    }),
    computed: {
        mousePX() {
            return this.mouseX / this.width;
        },
        mousePY() {
            return this.mouseY / this.height;
        },
        cardStyle() {
            const rX = this.mousePX * 5;
            const rY = this.mousePY * -5;
            return {
                transform: `rotateY(${rX}deg) rotateX(${rY}deg) translateZ(0)`
            };
        }
    },
    watch: {
        mouseXEnter: function (newVal, oldVal) {
            if (oldVal === 0) {
                this.$anime({
                    targets: this.$data,
                    easing: "linear",
                    duration: 150,
                    mouseX: newVal,
                    complete: () => {
                        this.mouseXEnter = 0;
                    }
                });
            }
        },
        mouseYEnter: function (newVal, oldVal) {
            if (oldVal === 0) {
                this.$anime({
                    targets: this.$data,
                    easing: "linear",
                    duration: 150,
                    mouseY: newVal,
                    complete: () => {
                        this.mouseYEnter = 0;
                    }
                });
            }
        }
    },
    mounted() {
        this.width = this.$refs.card.offsetWidth;
        this.height = this.$refs.card.offsetHeight;
    },
    methods: {
        handleMouseMove(e) {
            if (this.mouseXEnter === 0) {
                this.mouseX = e.pageX - this.$refs.card.offsetLeft - this.width / 2;
                this.mouseY = e.pageY - this.$refs.card.offsetTop - this.height / 2;
            }
        },
        handleMouseEnter(e) {
            this.mouseXEnter = e.pageX - this.$refs.card.offsetLeft - this.width / 2;
            this.mouseYEnter = e.pageY - this.$refs.card.offsetTop - this.height / 2;
            clearTimeout(this.mouseLeaveDelay);
        },
        handleMouseLeave() {
            this.mouseLeaveDelay = setTimeout(() => {
                this.$anime({
                    targets: this.$data,
                    easing: "linear",
                    duration: 150,
                    mouseX: 0,
                    mouseY: 0
                });
            }, 100);
        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
$hoverEasing: cubic-bezier(0.23, 1, 0.32, 1);
$returnEasing: cubic-bezier(0.445, 0.05, 0.55, 0.95);
.tippy-card {
    display: inline-block;
    margin: 10px;
    transform: perspective(400px);
    transform-style: preserve-3d;
    cursor: pointer;
    width: 100%;

    &:hover {
        // .tippy-card__info {
        //     transform: translateY(0);
        // }
        // .tippy-card__info p {
        //     opacity: 1;
        // }
        // .tippy-card__info,
        // .tippy-card__info p {
        //     transition: 0.6s $hoverEasing;
        // }
        // .tippy-card__info:after {
        //     transition: 1s $hoverEasing;
        //     opacity: 1;
        //     transform: translateY(0);
        // }
        .tippy-card__bg {
            transition: 0.6s $hoverEasing, opacity 1s $hoverEasing;
            opacity: 0.8;
        }
        .tippy-card__inner {
            transition: 0.6s $hoverEasing, box-shadow 2s $hoverEasing;
        }
    }

    &__inner {
        position: relative;
        flex: 0 0 240px;
        width: 100%;
        background-color: #333;
        overflow: hidden;
        border-radius: 10px;
        box-shadow: rgba(0, 0, 0, 0.66) 0 14px 30px 0;
        transition: 0.15s $returnEasing;
    }

    &__bg {
        opacity: 0.5;
        position: relative;
        top: 0px;
        left: 0px;
        width: 100%;
        height: 340px;
        padding: 0px;
        transition: 1s $returnEasing, opacity 1s 0.15s $returnEasing;
        pointer-events: none;
    }

    &__info {
        padding: 20px;
        position: relative;
        bottom: 0;
        background: #fff;
        color: #111;
        transition: 0.6s 0.2s cubic-bezier(0.215, 0.61, 0.355, 1);
        width: calc(100% - 40px);

        // p {
        // opacity: 0;
        // text-shadow: rgba(black, 1) 0 2px 3px;
        // transition: 0.6s 0.2s cubic-bezier(0.215, 0.61, 0.355, 1);
        // }

        * {
            position: relative;
            z-index: 1;
        }

        // &:after {
        //     content: "";
        //     position: absolute;
        //     top: 0;
        //     left: 0;
        //     z-index: 0;
        //     width: 100%;
        //     height: 100%;
        //     background-image: linear-gradient(
        //         to bottom,
        //         transparent 0%,
        //         rgba(#000, 0.6) 100%
        //     );
        //     background-blend-mode: overlay;
        //     opacity: 0;
        //     transform: translateY(100%);
        //     transition: 1s 0.15s $returnEasing;
        // }
        h1 {
            font-size: 36px;
            font-weight: 700;
            margin: 0;
            // text-shadow: rgba(black, 0.5) 0 10px 10px;
        }
    }
}
</style>