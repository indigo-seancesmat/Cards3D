<template>
    <div id="app">
        <div class="row">
            <Card3DFull :bg-image="mountain"
                :depth-map="mountainDepth"
                :sensitivity="25">
                <h1 slot="header">Mountains</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </Card3DFull>
            <TippyCardFull :bg-image="subway"
                :depth-map="subwayDepth"
                :sensitivity="25">
                <h1 slot="header">Subway</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCardFull>
        </div>
        <div class="row">
            <Card3DFull :bg-image="mountain"
                :depth-map="mountainDepth"
                :border-radius="10"
                :sensitivity="25">
                <h1 slot="header">Mountains</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </Card3DFull>
            <TippyCardFull :bg-image="subway"
                :depth-map="subwayDepth"
                :border-radius="10"
                :sensitivity="25">
                <h1 slot="header">Subway</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCardFull>
        </div>
        <h3 style="margin-top: 100px">The following are the same just different images and
            border-radius</h3>
        <div class="row">
            <Card3D :bg-image="boarder"
                :depth-map="boarderDepth"
                :sensitivity="60">
                <h1 slot="header">Snowboarder</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </Card3D>
            <TippyCard :bg-image="shelf"
                :depth-map="shelfDepth"
                :sensitivity="40"
                xymove>
                <h1 slot="header">Shelf</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
        </div>
        <div class="row">
            <Card3D :bg-image="subway"
                :depth-map="subwayDepth"
                :border-radius="10"
                :sensitivity="35">
                <h1 slot="header">Subway</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </Card3D>
            <TippyCard :bg-image="controller"
                :depth-map="controllerDepth"
                :border-radius="10"
                :sensitivity="40">
                <h1 slot="header">Games</h1>
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
            <TippyCard :bg-image="subway"
                :depth-map="subwayDepth"
                :border-radius="6"
                :sensitivity="30">
                <h1 slot="header">Subway</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
            <TippyCard :bg-image="subway"
                :depth-map="subwayDepth"
                :border-radius="6"
                :sensitivity="30"
                xymove>
                <h1 slot="header">Subway</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
        </div>
        <div class="row">
            <TippyCard :bg-image="mountain"
                :depth-map="mountainDepth"
                :border-radius="6"
                :sensitivity="30">
                <h1 slot="header">Mountain</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
            <TippyCard :bg-image="mountain"
                :depth-map="mountainDepth"
                :border-radius="6"
                :sensitivity="30"
                xymove>
                <h1 slot="header">Mountain</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
        </div>
        <!-- <div class="row">
            <TippyCard :bg-image="flowers"
                :depth-map="flowersDepth"
                :border-radius="6"
                :sensitivity="30">
                <h1 slot="header">Flowers</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
            <TippyCard :bg-image="flowers"
                :depth-map="flowersDepth"
                :border-radius="6"
                :sensitivity="30"
                xymove>
                <h1 slot="header">Flowers</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
        </div> -->
        <!-- <div class="row">
            <TippyCard :bg-image="boarder"
                :depth-map="boarderDepth"
                :border-radius="6"
                :sensitivity="50">
                <h1 slot="header">Boarder</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
            <TippyCard :bg-image="boarder"
                :depth-map="boarderDepth"
                :border-radius="6"
                :sensitivity="50"
                xymove>
                <h1 slot="header">Boarder</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </TippyCard>
        </div> -->
        <h3 style="margin: 100px auto 0px; max-width: 752px;">The following is to show a version
            with a popup info box</h3>
        <div class="row">
            <Card3D :bg-image="boarder"
                :depth-map="boarderDepth"
                :border-radius="6"
                :sensitivity="50"
                info-popup>
                <h1 slot="header">Boarder</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
            </Card3D>
            <TippyCard :bg-image="boarder"
                :depth-map="boarderDepth"
                :border-radius="6"
                :sensitivity="50"
                xymove
                info-popup>
                <h1 slot="header">Boarder</h1>
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
            flowersDepth
        };
    }
};
</script>

<style>
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

h3 {
    color: #41b3a3;
}
</style>
