<template>
    <div id="app">
        <div class="row">
            <Card3DFull :bg-image="mountain"
                :depth-map="mountainDepth"
                :sensitivity="25">
                <h1 slot="header">Mountains</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
            </Card3DFull>
            <TippyCardFull :bg-image="subway"
                :depth-map="subwayDepth"
                :sensitivity="25">
                <h1 slot="header">Subway</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
            </TippyCardFull>
        </div>
        <h3 style="margin-top: 100px">The following are the same just different images</h3>
        <div class="row">
            <Card3D :bg-image="boarder"
                :depth-map="boarderDepth"
                :sensitivity="60">
                <h1 slot="header">Snowboarder</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
            </Card3D>
            <TippyCard :bg-image="shelf"
                :depth-map="shelfDepth"
                :sensitivity="40"
                xymove>
                <h1 slot="header">Shelf</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
            </TippyCard>
        </div>
        <div class="row">
            <Card3D :bg-image="subway"
                :depth-map="subwayDepth"
                :sensitivity="35">
                <h1 slot="header">Subway</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
            </Card3D>
            <TippyCard :bg-image="controller"
                :depth-map="controllerDepth"
                :sensitivity="40">
                <h1 slot="header">Games</h1>
                <p slot="content">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
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
            shelfDepth
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
</style>
