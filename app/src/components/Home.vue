<template>
  <header id="header">
    <Menu />

    <div class="container">
      <div class="vintage_corner_right">
        <img src="../assets/img/vintage_corner_right.svg" alt="corner" />
      </div>
      <div class="header-content">
        <h1>I Build Amazing Experiences</h1>
        <p class="lead">Specialized in Web Development</p>
        <a href="#projects" class="button">View My Work</a>
      </div>
    </div>

    <div class="abstract_shapes">
      <div class="bg0">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bg1">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bg2">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bg2">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bg3">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bg4">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bg3">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bg4">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bg5">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bg6">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
    </div>

    <div class="abstract_opac">
      <div class="bgA">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bgB">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bgC">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
    </div>
    <div class="abstract_opac2">
      <div class="bgD">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bgE">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
      <div class="bgF">
        <img :src="mainSVG" :alt="mainSVG" />
      </div>
    </div>
  </header>
</template>

<script>
// @ is an alias to /src
import Menu from "@/components/Menu.vue";
import { gsap } from "gsap";
import { TextPlugin } from "gsap/TextPlugin";
gsap.registerPlugin(TextPlugin);
import mainSVG from "../assets/img/bigRec-01.svg";

export default {
  name: "Home",
  data() {
    return {
      mainSVG: mainSVG
    };
  },
  components: {
    Menu
  },
  methods: {
    /* ========================================================================================= */
    // ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    // Header Content: h1 and .lead paragraph Animation~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    h1Animation() {
      let h1Time = gsap.timeline({
        defaults: { opacity: 0, ease: "linear", autoAlpha: 0 }
      });
      let h1 = document.querySelector(".container .header-content h1"); // h1
      h1Time.from(h1, {
        duration: 1,
        scale: 0,
        transformOrigin: "50% 50%",
        stagger: 0.5
      });
    },
    animSub() {
      // let subTimeline = gsap.timeline({ defaults: { opacity: 0, ease: "power2.out" } });
      let subTimeline = gsap.timeline({
        defaults: { opacity: 0.8, ease: "sine.out" }
      });
      subTimeline.addPause(8).to(
        ".lead", // paragraph
        {
          ease: "sine.out",
          duration: 3,
          color: "bisque",
          text: "Love Everything about Creativity",
          stagger: 0.5
        },
        "-=3"
      );
    },
    loadShapes() {
      let imgtl = gsap.timeline({
        defaults: { opacity: 0, ease: "power2.out", autoAlpha: 0 }
      });
      let abstractShapes = document.querySelector(".abstract_shapes");
      let imgShapes0 = document.querySelectorAll(".abstract_shapes .bg0");
      let imgShapes1 = document.querySelectorAll(".abstract_shapes .bg1");
      let imgShapes2 = document.querySelectorAll(".abstract_shapes .bg2");
      let imgShapes3 = document.querySelectorAll(".abstract_shapes .bg3");
      let imgShapes4 = document.querySelectorAll(".abstract_shapes .bg4");
      let imgShapes5 = document.querySelectorAll(".abstract_shapes .bg5");
      let imgShapes6 = document.querySelectorAll(".abstract_shapes .bg6");

      imgtl
        .from(
          abstractShapes,
          {
            duration: 2.5,
            opacity: 0.5,
            yoyo: true,
            repeat: -1,
            stagger: 0.7,
            autoAlpha: 0
          },
          "-=2"
        )
        .from(imgShapes0, {
          duration: 1,
          scale: 0,
          ease: "linear",
          x: -300,
          stagger: 0.5,
          autoAlpha: 0
        })
        .from(
          imgShapes1,
          {
            duration: 1,
            scale: 0,
            ease: "linear",
            x: 300,
            stagger: 0.5,
            autoAlpha: 0
          },
          "-=1"
        )
        .from(
          imgShapes2,
          {
            duration: 3.5,
            transformOrigin: "50% 50%",
            scale: 0.2,
            ease: "linear",
            stagger: 0.5,
            rotation: 360,
            autoAlpha: 0
          },
          "-=1.5"
        )
        .from(
          imgShapes3,
          {
            duration: 2,
            scale: 0,
            ease: "linear",
            x: -200,
            stagger: 0.5,
            rotation: -360,
            autoAlpha: 0
          },
          "-=1.5"
        )
        .from(
          imgShapes4,
          {
            duration: 2,
            scale: 0,
            ease: "linear",
            x: 200,
            stagger: 0.5,
            rotation: 360,
            autoAlpha: 0
          },
          "-=1.5"
        )
        .from(
          imgShapes5,
          {
            duration: 2,
            scale: 0,
            ease: "linear",
            x: -200,
            stagger: 0.5,
            rotation: -360,
            autoAlpha: 0
          },
          "-=1.5"
        )
        .from(
          imgShapes6,
          {
            duration: 2,
            scale: 0,
            ease: "linear",
            x: 200,
            stagger: 0.5,
            rotation: 360,
            autoAlpha: 0
          },
          "-=1.5"
        );
    }
  },
  mounted: function() {
    this.h1Animation();
    this.animSub();
    this.loadShapes();
  }
};
</script>

<style scoped>
#header {
  height: 100vh;
  position: relative;
}
/* ========================================================================================= */
/* ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Abstract golden animated shapes~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ */
.abstract_shapes {
  visibility: hidden;
}
.abstract_shapes .bg0 {
  position: absolute;
  bottom: 38%;
  right: 13%;
  width: 15%;
  height: 50%;
  visibility: hidden;
  /* background-color: violet; */
}
.abstract_shapes .bg1 {
  position: absolute;
  bottom: 0%;
  right: 13%;
  width: 15%;
  height: 32%;
  visibility: hidden;
  /* background-color: orange; */
}
.abstract_shapes .bg2 {
  position: absolute;
  bottom: 28%;
  right: 13%;
  width: 15%;
  height: 32%;
  visibility: hidden;
  /* background: green; */
}
.abstract_shapes .bg3 {
  position: absolute;
  bottom: 24%;
  right: 22%;
  width: 10%;
  height: 45%;
  visibility: hidden;
  /* background-color: yellow; */
}
.abstract_shapes .bg4 {
  position: absolute;
  bottom: 11%;
  right: 9%;
  width: 10%;
  height: 30%;
  visibility: hidden;
}
.abstract_shapes .bg5 {
  position: absolute;
  bottom: 11%;
  right: 22%;
  width: 10%;
  height: 30%;
  visibility: hidden;
}
.abstract_shapes .bg6 {
  position: absolute;
  bottom: 39%;
  right: 9%;
  width: 10%;
  height: 30%;
  visibility: hidden;
}
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Abstract Opac dimmed Ornament Shapes~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
.abstract_opac .bgA {
  position: fixed;
  top: 15%;
  left: 23%;
  width: 5rem;
  opacity: 0.2;
}
.abstract_opac .bgB {
  position: fixed !important;
  top: 40%;
  left: 14%;
  width: 8rem;
  opacity: 0.2;
}
.abstract_opac .bgC {
  position: fixed !important;
  top: 25%;
  left: 18%;
  width: 12rem;
  opacity: 0.2;
}
.abstract_opac2 .bgD {
  position: fixed;
  bottom: 20%;
  left: 18%;
  width: 6rem;
  opacity: 0.2;
}
.abstract_opac2 .bgE {
  position: fixed;
  top: 30%;
  left: 25%;
  width: 8rem;
  opacity: 0.2;
}
.abstract_opac2 .bgF {
  position: fixed;
  top: 50%;
  left: 18%;
  width: 12rem;
  opacity: 0.2;
}
.vintage_corner_right {
  position: absolute;
  bottom: 0;
  right: 3%;
}

/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Header Content~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ */
.container .header-content {
  height: 100vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  text-align: center;
}
.container .header-content h1 {
  max-width: 600px;
  visibility: hidden; /*using for animation;*/
}
.container .header-content p {
  margin: 20px 0 30px;
}
/* eslint-disable-next-line */
/* eslint-disable */

/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Responsive Layout~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Smartphones ~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (max-width: 500px) {
  body {
    /* background-color: green;  fixed added final touches */
  }
  h1 {
    font-size: 3rem;
    padding-bottom: 1rem;
    font-weight: lighter;
  }
  h2 {
    font-size: 2.2rem;
    font-weight: lighter;
    padding: 1rem 0;
  }
  h3 {
    font-size: 1.8rem;
    font-weight: lighter;
    padding-bottom: 1rem;
  }
  p {
    font-size: 1.2rem;
    padding-bottom: 1.2rem;
  }
  .abstract_shapes {
    display: none;
  }
  .container .header-content h1 {
    font-size: 3rem;
    max-width: 600px;
    font-weight: lighter;
    line-height: 1.2;
    visibility: hidden; /*using for animation;*/
    margin-bottom: 20px;
  }
  .container .header-content p {
    /* max-width: 450px; */
    padding: 0 1rem;
  }
  /*~~~~~~~~~~~~~~~~~~~~~~~~~~~Abstract Opac background Shapes~~~~~~~~~~~~~~~~~~~~~~*/
  .abstract_opac2 {
    display: none;
  }
  .vintage_corner_right {
    display: none;
  }
  .vintage_corner_top {
    display: none;
  }
}

/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Tablets~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (min-width: 501px) and (max-width: 768px) {
  h1 {
    font-size: 3rem;
    padding-bottom: 1rem;
    font-weight: lighter;
  }
  h2 {
    font-size: 2.5rem;
    font-weight: lighter;
    padding: 1.5rem 0;
  }
  h3 {
    font-size: 1.8rem;
    font-weight: lighter;
    padding-bottom: 1rem;
  }
  body {
    font-size: 1.5rem;
    overflow-x: hidden;
    /* background-color: blueviolet; */
  }
  .container .header-content h1 {
    font-size: 3.5rem;
    max-width: 700px;
    font-weight: lighter;
    line-height: 1.4;
    visibility: hidden; /*using for animation;*/
    margin-bottom: 20px;
  }
  .container .header-content p {
    /* max-width: 400px; */
    padding: 0 1rem;
    margin: 20px 0 30px;
  }
  /*~~~~~~~~~~~~~~~~~~~~~~~~~~~Abstract Opac background Shapes~~~~~~~~~~~~~~~~~~~~~~*/
  .abstract_opac .bgC {
    position: fixed;
    top: 30%;
    left: 14%;
    width: 12rem;
    opacity: 0.2;
  }
  .abstract_opac .bgD {
    position: fixed;
    top: 34%;
    left: 12%;
    width: 5rem;
    opacity: 0.2;
    z-index: 1000;
  }
  .abstract_opac .bgE {
    position: fixed;
    top: 60%;
    left: 20%;
    width: 8rem;
    opacity: 0.2;
  }
  .abstract_opac .bgF {
    position: fixed;
    top: 140%;
    left: 4%;
    width: 12rem;
    opacity: 0.2;
  }
}
/* ========================================================================================= */
/* ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Tablet other sizes~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ */
@media (min-width: 599px) and (max-width: 960) {
  body {
    /* background-color: rgb(76, 23, 126); */
    font-size: 1.5rem;
    overflow-x: hidden;
  }
  .container .header-content h1 {
    font-size: 3rem;
    max-width: 700px;
    font-weight: lighter;
    line-height: 1.4;
    visibility: hidden; /*using for animation;*/
    margin-bottom: 20px;
  }
  .container .header-content p {
    max-width: 400px;
    margin: 20px 0 30px;
  }
  /*~~~~~~~~~~~~~~~~~~~~~~~~~~~Abstract Opac background Shapes~~~~~~~~~~~~~~~~~~~~~~*/
  .abstract_opac .bgC {
    position: fixed;
    top: 30%;
    left: 14%;
    width: 12rem;
    opacity: 0.2;
  }
  .abstract_opac .bgD {
    position: fixed;
    top: 34%;
    left: 12%;
    width: 5rem;
    opacity: 0.2;
    z-index: 1000;
  }
  .abstract_opac .bgE {
    position: fixed;
    top: 60%;
    left: 20%;
    width: 8rem;
    opacity: 0.2;
  }
  .abstract_opac .bgF {
    position: fixed;
    top: 140%;
    left: 4%;
    width: 12rem;
    opacity: 0.2;
  }
}
/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Normal  Screens~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (min-width: 769px) and (max-width: 1200px) {
  body {
    /* background-color: burlywood; */
  }
  /*~~~~~~~~~~~~~~~~~~~~~~ Abstract Opac background Shapes~~~~~~~~~~~~~~~~~~~~~~~~*/
  .abstract_opac .bgC {
    position: fixed;
    top: 30%;
    left: 14%;
    width: 12rem;
    opacity: 0.2;
  }
  .abstract_opac .bgD {
    position: fixed;
    top: 34%;
    left: 12%;
    width: 5rem;
    opacity: 0.2;
  }
  .abstract_opac .bgE {
    position: fixed;
    top: 60%;
    left: 20%;
    width: 8rem;
    opacity: 0.2;
  }
  .abstract_opac .bgF {
    position: fixed;
    top: 140%;
    left: 4%;
    width: 12rem;
    opacity: 0.2;
  }
}
/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Widescreens~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~Abstract Opac background Shapes~~~~~~~~~~~~~~~~~~~~~~*/
@media (min-width: 1201px) {
  .abstract_opac .bgA {
    position: fixed;
    top: 30%;
    left: 6%;
    width: 5rem;
    opacity: 0.2;
  }
  .abstract_opac .bgB {
    position: fixed;
    top: 20%;
    left: 8%;
    width: 8rem;
    opacity: 0.2;
  }
  .abstract_opac .bgC {
    position: fixed;
    top: 30%;
    left: 10%;
    width: 12rem;
    opacity: 0.2;
  }

  .vintage_corner_right {
    position: absolute;
    bottom: 0;
    right: 1.2%;
  }
}
</style>
