<template>
    <div id="app">
        <div id="nav">

            <div>
                Image:
                <button @click="setImage('subway')"
                    :class="{active: currentBGName === 'subway'}">Subway</button>
                <button @click="setImage('mountain')"
                    :class="{active: currentBGName === 'mountain'}">Mountain</button>
                <button @click="setImage('boarder')"
                    :class="{active: currentBGName === 'boarder'}">Boarder</button>
                <button @click="setImage('controller')"
                    :class="{active: currentBGName === 'controller'}">Controller</button>
                <button @click="setImage('shelf')"
                    :class="{active: currentBGName === 'shelf'}">Shelf</button>
            </div>
            <div>

                <strong>Border-Radius:</strong>
                <input type="text"
                    v-model="borderRadius"
                    style="max-width: 30px; margin-left: 10px">
            </div>
            <div>
                <strong>Sensitivity:</strong>
                <input type="text"
                    v-model="sensitivity"
                    style="max-width: 30px; margin-left: 10px">
                <span style="font-size: 12px; padding-left: 5px">(lower number = more
                    sensitive)</span>
                <span style="font-size: 12px; padding-left: 5px">Recommended for this image:
                    <strong style="color: #3bef9d;">{{ recommendedSensitivity }}</strong></span>
            </div>

        </div>
        <div class="row"
            style="margin-top: 140px;">
            <Card3DFull :key="`Card3DFull-${currentBGName}`"
                :bg-image="currentBG"
                :depth-map="currentBGDepth"
                :border-radius="borderRadius"
                :sensitivity="sensitivity">
                <h1 slot="header">{{ currentBGName }}</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </Card3DFull>
            <TippyCardFull :key="`TippyCardFull-${currentBGName}`"
                :bg-image="currentBG"
                :depth-map="currentBGDepth"
                :border-radius="borderRadius"
                :sensitivity="sensitivity">
                <h1 slot="header">{{ currentBGName }}</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCardFull>
        </div>
        <h3 style="margin-top: 100px">With a persistant info box</h3>
        <div class="row">
            <Card3D :key="`Card3D-A-${currentBGName}`"
                :bg-image="currentBG"
                :depth-map="currentBGDepth"
                :border-radius="borderRadius"
                :sensitivity="sensitivity">
                <h1 slot="header">{{ currentBGName }}</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </Card3D>
            <TippyCard :key="`TippyCard-A-${currentBGName}`"
                :bg-image="currentBG"
                :depth-map="currentBGDepth"
                :border-radius="borderRadius"
                :sensitivity="sensitivity">
                <h1 slot="header">{{ currentBGName }}</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
        </div>
        <h3 style="margin: 100px auto 0px; max-width: 752px;">With a popup info box</h3>
        <div class="row"
            style="margin-bottom: 100px;">
            <Card3D :key="`Card3D-C-${currentBGName}`"
                :bg-image="currentBG"
                :depth-map="currentBGDepth"
                :border-radius="borderRadius"
                :sensitivity="sensitivity"
                info-popup>
                <h1 slot="header">{{ currentBGName }}</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </Card3D>
            <TippyCard :key="`TippyCard-C-${currentBGName}`"
                :bg-image="currentBG"
                :depth-map="currentBGDepth"
                :border-radius="borderRadius"
                :sensitivity="sensitivity"
                xymove
                info-popup>
                <h1 slot="header">{{ currentBGName }}</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
        </div>
        <h3 style="margin: 100px auto 0px; max-width: 752px;">The following are comparing the fake
            3D effect on its own and moving the image around while still using the fake 3D
            effect</h3>
        <div class="row">
            <h2 style="text-align: center; width: 100%; margin: 20px 0 0 0;">Fake 3D</h2>
            <h2 style="text-align: center; width: 100%; margin: 20px 0 0 0;">Fake 3D with Image
                shifting</h2>
        </div>
        <div class="row">
            <TippyCard :key="`TippyCard-B-${currentBGName}`"
                :bg-image="currentBG"
                :depth-map="currentBGDepth"
                :border-radius="borderRadius"
                :sensitivity="sensitivity">
                <h1 slot="header">{{ currentBGName }}</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
            <TippyCard :key="`TippyCardXYMove-${currentBGName}`"
                :bg-image="currentBG"
                :depth-map="currentBGDepth"
                :border-radius="borderRadius"
                :sensitivity="sensitivity"
                xymove>
                <h1 slot="header">{{ currentBGName }}</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
        </div>
    </div>
</template>

<script>
import TippyCardFull from "./components/TippyCardFull";
import TippyCard from "./components/TippyCard";
import Card3DFull from "./components/Card3DFull";
import Card3D from "./components/Card3D";
import subway from "@/assets/subway.jpg";
import subwayDepth from "@/assets/subway-depth.jpg";
import mountain from "@/assets/mountain.jpg";
import mountainDepth from "@/assets/mountain-depth.jpg";
import controller from "@/assets/controller.jpg";
import controllerDepth from "@/assets/controller-depth.jpg";
import boarder from "@/assets/boarder.jpg";
import boarderDepth from "@/assets/boarder-depth.jpg";
import shelf from "@/assets/shelf-blur.jpg";
import shelfDepth from "@/assets/shelf-depth.jpg";
import flowers from "@/assets/flowers.jpg";
import flowersDepth from "@/assets/flowers-depth.jpg";

export default {
    name: "App",
    components: {
        TippyCardFull,
        TippyCard,
        Card3DFull,
        Card3D
    },
    data() {
        return {
            subway,
            subwayDepth,
            mountain,
            mountainDepth,
            controller,
            controllerDepth,
            boarder,
            boarderDepth,
            shelf,
            shelfDepth,
            flowers,
            flowersDepth,
            currentBG: subway,
            currentBGDepth: subwayDepth,
            currentBGName: 'subway',
            borderRadius: 10,
            sensitivity: 30,
            recommendedSensitivity: 30
        };
    },
    methods: {
        setImage(name) {
            if (name === 'subway') {
                this.currentBG = subway;
                this.currentBGDepth = subwayDepth;
                this.currentBGName = 'subway';
                this.recommendedSensitivity = 30;
            }
            if (name === 'mountain') {
                this.currentBG = mountain;
                this.currentBGDepth = mountainDepth;
                this.currentBGName = 'mountain';
                this.recommendedSensitivity = 45;
            }
            if (name === 'boarder') {
                this.currentBG = boarder;
                this.currentBGDepth = boarderDepth;
                this.currentBGName = 'boarder';
                this.recommendedSensitivity = 60;
            }
            if (name === 'controller') {
                this.currentBG = controller;
                this.currentBGDepth = controllerDepth;
                this.currentBGName = 'controller';
                this.recommendedSensitivity = 45;
            }
            if (name === 'shelf') {
                this.currentBG = shelf;
                this.currentBGDepth = shelfDepth;
                this.currentBGName = 'shelf';
                this.recommendedSensitivity = 50;
            }
        }
    }
};
</script>

<style lang="scss">
#app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
.row {
    max-width: 1080px;
    margin: 0 auto;
    display: flex;
}
h1 {
    text-transform: capitalize;
}
h3 {
    color: #41b3a3;
}

#nav {
    position: fixed;
    width: 100%;
    z-index: 100;
    top: 0;
    left: 0;
    display: flex;
    justify-content: space-around;
    padding: 16px 30px;
    background: rgba(0, 0, 0, 0.75);
    backdrop-filter: blur(10px);
    color: #fff;
    a {
        font-weight: bold;
        color: #fff;

        &.router-link-exact-active {
            color: #3bef9d;
        }
    }
    .active {
        background: #3bef9d;
    }
    button {
        padding: 5px 10px;
        display: inline-block;
        border-radius: 3px;
        border: none;
        background: #ccc;
        font-size: 12px;
        font-weight: bold;
        color: #333;
        margin-left: 4px;
        margin-right: 4px;
        cursor: pointer;
        &:hover {
            background: #54f7ae;
        }
    }
    input[type="text"] {
        background: #3bef9d;
        font-weight: bold;
        font-size: 14px;
        border: none;
        text-align: center;
    }
}
</style>
