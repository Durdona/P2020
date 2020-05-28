<template>
  <!-- About Me Section -->
  <section class="about" id="about-me">
    <div class="container">
      <div class="vintage_corner_top">
        <img src="../assets/img/vintage_corner_top.svg" alt="corner" />
      </div>
      <div class="about_title">
        <h2>About Me</h2>
        <p>A highly talented self-taught Front-End Web Developer who is eager to be a great teammate and solid contributor.</p>
        <div id="skills">
          <h3>Skills I have</h3>
          <div class="skills-list">
            <div class="skills-list-a">
              <p id="html">.........................</p>
              <p id="css">.........................</p>
              <p id="js">.........................</p>
              <p id="react">.........................</p>
            </div>
            <div class="skills-list-b">
              <p id="vue">.........................</p>
              <p id="axios">.........................</p>
              <p id="leaflet">.........................</p>
              <p id="gsap">.........................</p>
            </div>
          </div>
        </div>
      </div>
      <!-- Projects -->
      <div class="about_pages" id="projects">
        <div class="project project1">
          <figure class="img-figure">
            <img src="../assets/img/responsive.png" alt />
            <figcaption>
              <h3>Project One</h3>
              <p>
                Lorem ipsum, elit. Rerum quia suscipit earum pariatur quo
                .
              </p>
              <div class="icons">
                <i class="fab fa-github"></i>
                <i class="fab fa-codepen"></i>
              </div>
            </figcaption>
          </figure>
        </div>

        <div class="project project2">
          <figure class="img-figure">
            <img src="../assets/img/responsive.png" alt />
            <figcaption>
              <h3>Project Two</h3>
              <p>
                Lorem ipsum, elit. Rerum quia suscipit earum pariatur quo
                .
              </p>
              <div class="icons">
                <i class="fab fa-github"></i>
                <i class="fab fa-codepen"></i>
              </div>
            </figcaption>
          </figure>
        </div>

        <div class="project project3">
          <figure class="img-figure">
            <img src="../assets/img/responsive.png" alt />
            <figcaption>
              <h3>Project Three</h3>
              <p>
                Lorem ipsum, elit. Rerum quia suscipit earum pariatur quo
                .
              </p>
              <div class="icons">
                <i class="fab fa-github"></i>
                <i class="fab fa-codepen"></i>
              </div>
            </figcaption>
          </figure>
        </div>

        <div class="project project4">
          <figure class="img-figure">
            <img src="../assets/img/responsive.png" alt="showcase" />
            <figcaption>
              <h3>
                Portfolio
                <i class="far fa-calendar-alt"></i>
              </h3>
              <p>Fully Responsive. Coded in Vue.JS, HTML5, CSS3, GSAP, Vanilla JavaScript</p>
              <div class="icons">
                <i class="fab fa-github"></i>
                <i class="fab fa-codepen"></i>
              </div>
            </figcaption>
          </figure>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { gsap } from "gsap";
import { TextPlugin } from "gsap/TextPlugin";
gsap.registerPlugin(TextPlugin);
import * as ScrollMagic from "scrollmagic";
import { TweenMax, TimelineMax } from "gsap"; // Also works with TweenLite and TimelineLite
import { ScrollMagicPluginGsap } from "scrollmagic-plugin-gsap";
ScrollMagicPluginGsap(ScrollMagic, TweenMax, TimelineMax);

export default {
  name: "About",
  methods: {
    /* ========================================================================================= */
    // ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    // Scroll Parallax Effect ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    scroll() {
      let query = window.matchMedia("(min-width: 769px)");

      if (query.matches) {
        const controller = new ScrollMagic.Controller();

        new ScrollMagic.Scene({
          // pinning .about_title
          duration: "210%",
          triggerElement: ".about_title",
          triggerHook: 0
        })
          .setPin(".about_title", { pushFollowers: false })
          .addTo(controller);
        // .addIndicators()

        new ScrollMagic.Scene({
          //pinning vintage ornament
          duration: "240%",
          triggerElement: ".vintage_corner_top",
          triggerHook: 0
        })
          .setPin(".vintage_corner_top", { pushFollowers: false })
          .addTo(controller);

        //animating h2 of about section on scrolling
        let h2tl = gsap.timeline({
          defaults: { opacity: 0, ease: "linear", autoAlpha: 0 }
        });
        h2tl.from(".about_title h2", {
          duration: 1,
          scale: 0,
          transformOrigin: "50% 50%",
          stagger: 0.5
        });
        new ScrollMagic.Scene({
          // animating h2 inside about section
          triggerElement: ".about_title h2",
          triggerHook: 0.9
        })
          .setTween(h2tl)
          .addTo(controller);
      }
    }
  },
  mounted: function() {
    this.scroll();
    /* ========================================================================================= */
    //~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    // `````````````````````````````````````````````````````````````````````````````````````````````
    //Adding Typing Effect for About Me Listed Skills on Scrolling Event
    const skillsController = new ScrollMagic.Controller();
    let skillHTML = gsap.timeline();
    gsap.set(".skills-list-a ", { autoAlpha: 1 });
    function skillHTMLfunction() {
      skillHTML.to("#html", {
        ease: "sine.out",
        duration: 4,
        color: "bisque",
        text: "HTML",
        stagger: 1,
        opacity: 1,
        scale: 1
      });
    }
    // scene for HTML skills text  (Typing Effect)
    new ScrollMagic.Scene({
      triggerElement: "#html",
      triggerHook: 0.5
    })
      .setTween(skillHTML)
      .addTo(skillsController);
    skillHTMLfunction(); // without using function I was getting warning in the console !

    // ```````````````````````````````````````````````````````````````````````````````````````````````````
    let skillCSS = gsap.timeline();
    function skillCSSfunction() {
      skillCSS.to("#css", {
        ease: "sine.out",
        duration: 4,
        color: "bisque",
        text: "CSS",
        stagger: 0.5
      });
    }
    // scene for CSS skills text  (Typing Effect)
    new ScrollMagic.Scene({
      triggerElement: "#css",
      triggerHook: 0.6
    })
      .setTween(skillCSS)
      .addTo(skillsController);
    // .addIndicators();
    skillCSSfunction(); // without using function I was getting warning in the console !

    // ````````````````````````````````````````````````````````````````````````````````````````````````
    let skillJS = gsap.timeline();
    function skillJSfunction() {
      skillJS.to("#js", {
        ease: "sine.out",
        duration: 3,
        color: "bisque",
        text: "JavaScript",
        stagger: 0.5
      });
    }
    // scene for JS skills text  (Typing Effect)
    new ScrollMagic.Scene({
      triggerElement: "#js",
      triggerHook: 0.7
    })
      .setTween(skillJS)
      .addTo(skillsController);
    skillJSfunction(); // without using function I was getting warning in the console !

    // `````````````````````````````````````````````````````````````````````````````````````````````````
    let skillReact = gsap.timeline();
    function skillReactfunction() {
      skillReact.to("#react", {
        ease: "sine.out",
        duration: 3,
        color: "bisque",
        text: "React.JS",
        stagger: 1
      });
    }
    // scene for React.JS skills text  (Typing Effect)
    new ScrollMagic.Scene({
      triggerElement: "#react",
      triggerHook: 0.7
    })
      .setTween(skillReact)
      .addTo(skillsController);
    skillReactfunction(); // without using function I was getting warning in the console !

    // ````````````````````````````````````````````````````````````````````````````````````````````````````
    let skillVue = gsap.timeline();
    function skillVuefunction() {
      skillVue.to("#vue", {
        ease: "sine.out",
        duration: 4,
        color: "bisque",
        text: "Vue.JS",
        stagger: 0.5
      });
    }
    // scene for Vue.JS skills text  (Typing Effect)
    new ScrollMagic.Scene({
      triggerElement: "#vue",
      triggerHook: 0.5
    })
      .setTween(skillVue)
      .addTo(skillsController);
    skillVuefunction(); // without using function I was getting warning in the console !

    // ````````````````````````````````````````````````````````````````````````````````````````````````````
    let skillAxios = gsap.timeline();
    function skillAxiosfunction() {
      skillAxios.to("#axios", {
        ease: "sine.out",
        duration: 3,
        color: "bisque",
        text: "Axios",
        stagger: 0.5
      });
    }
    // scene for Axios skills text  (Typing Effect)
    new ScrollMagic.Scene({
      triggerElement: "#axios",
      triggerHook: 0.6
    })
      .setTween(skillAxios)
      .addTo(skillsController);

    skillAxiosfunction(); // without using function I was getting warning in the console !

    // `````````````````````````````````````````````````````````````````````````````````````````````````````
    let skillLeaflet = gsap.timeline();
    function skillLeafletfunction() {
      skillLeaflet.to("#leaflet", {
        ease: "sine.out",
        duration: 3,
        color: "bisque",
        text: "Leaflet.JS",
        stagger: 0.5
      });
    }
    // scene for Leaflet skills text  (Typing Effect)
    new ScrollMagic.Scene({
      triggerElement: "#leaflet",
      triggerHook: 0.7
    })
      .setTween(skillLeaflet)
      .addTo(skillsController);
    skillLeafletfunction(); // without using function I was getting warning in the console !

    // `````````````````````````````````````````````````````````````````````````````````````````````````````
    let skillGSAP = gsap.timeline();
    function skillGSAPfunction() {
      skillGSAP.to("#gsap", {
        ease: "sine.out",
        duration: 4,
        color: "bisque",
        text: "GSAP  ",
        stagger: 1
      });
    }
    // scene for Axios skills text  (Typing Effect)
    new ScrollMagic.Scene({
      triggerElement: "#gsap",
      triggerHook: 0.7
    })
      .setTween(skillGSAP)
      .addTo(skillsController);
    // .addIndicators();
    skillGSAPfunction(); // without using function I was getting warning in the console !

    // =============================================================================================
    // ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    // Projects are being animated on Scrolling Event ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    const projectController = new ScrollMagic.Controller();
    // project1 showcase is being animated
    let project1 = document.querySelector(".project1 .img-figure");
    new ScrollMagic.Scene({
      triggerElement: project1,
      triggerHook: 0.9
    })
      .setClassToggle(".project1", "fade-in")
      .addTo(projectController);

    // project2 showcase is being animated when scrolling
    let pr2tl = gsap.timeline();
    pr2tl.from(".project2 .img-figure", {
      duration: 1.5,
      scale: 0.5,
      transformOrigin: "50% 50%",
      stagger: 0.5,
      opacity: 0
    });
    new ScrollMagic.Scene({
      triggerElement: ".project2 .img-figure",
      triggerHook: 0.9
    })
      .setTween(pr2tl)
      .addTo(projectController);

    // project3 showcase is being animated when scrolling
    new ScrollMagic.Scene({
      triggerElement: ".project3 .img-figure",
      triggerHook: 0.9
    })
      .setClassToggle(".project3", "fade-in")
      .addTo(projectController);

    // project4 showcase is being animated when scrolling
    new ScrollMagic.Scene({
      triggerElement: ".project4 .img-figure",
      triggerHook: 0.9
    })
      .setClassToggle(".project4", "fade-in")
      .addTo(projectController);
  }
};
</script>


<style scoped>
/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ About Section~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
/* ========================================================================================= */
section.about .container {
  background-color: rgba(2, 4, 41, 0.7);
}
section.about .vintage_corner_top {
  position: absolute;
  left: 1%;
}
section.about .about_title {
  display: flex;
  flex-direction: column;
  width: 100%;
  text-align: center;
  position: relative;
}
section.about .about_title p {
  padding: 0 2rem 2rem 2rem;
}
section.about .about_title #skills {
  width: 100%;
}
section.about .about_title .skills-list {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  text-align: left;
}
.skills-list-a,
skills-list-b {
  visibility: hidden;
  /*  using it for animation */
  letter-spacing: 0;
}
section.about .about_pages div {
  height: 30vh;
  padding: 0 1rem 0;
}
section.about .about_pages .project {
  margin-bottom: 2rem;
}
section.about .about_pages .project1,
section.about .about_pages .project4 {
  opacity: 0;
  transform: translateX(100px);
  transition: all 1s ease-out;
}
section.about .about_pages .project1.fade-in,
section.about .about_pages .project4.fade-in {
  opacity: 1;
  transform: translateX(0);
}
section.about .about_pages .project3 {
  opacity: 0;
  transform: translateX(-100px);
  transition: all 1s ease-out;
}
section.about .about_pages .project3.fade-in {
  opacity: 1;
  transform: translateX(0);
}
section.about .about_pages .img-figure {
  position: relative;
  overflow: hidden;
  background: linear-gradient(to left, #0a011e, bisque);
  box-shadow: 2px 6px 25px rgba(255, 255, 255, 0.7);
  box-shadow: 2px 16px 25px rgba(0, 0, 0, 1);
  border-radius: 8px;
}
section.about .about_pages .img-figure * {
  transition: all 0.5s ease;
}
section.about .about_pages .img-figure img {
  max-width: 100%;
  backface-visibility: hidden;
  vertical-align: top;
}
section.about .about_pages .img-figure figcaption {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-direction: column;
  padding: 0 0.75rem;
  z-index: 1;
}
section.about .about_pages .img-figure .icons {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100px;
  margin-bottom: 1rem;
}
section.about .about_pages figcaption h3 .fa-calendar-alt {
  color: khaki;
  font-weight: lighter;
  padding-left: 10px;
}
section.about .about_pages figcaption h3 .fa-calendar-alt:after {
  content: "2020";
  padding-left: 10px;
  color: khaki;
}
section.about .about_pages .img-figure .icons .fa-github:hover,
section.about .about_pages .img-figure .icons .fa-codepen:hover {
  color: black;
  background-color: white;
  cursor: pointer;
  border-radius: 5px;
  padding: 2px;
  transition: all 0.2s ease;
}
section.about .about_pages .img-figure:after,
section.about .about_pages .img-figure figcaption {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}
section.about .about_pages .img-figure:after {
  content: "";
  background-image: url("../assets/img/projects_background.svg");
  background-repeat: no-repeat;
  background-attachment: scroll;
  background-position: 50% 50%;
  background-color: #0a051c;
  background-size: initial;
  transition: all 0.4s ease;
  opacity: 0;
}
section.about .about_pages .img-figure figcaption h3 {
  line-height: 1;
  opacity: 0;
  margin-bottom: 15px;
  width: 100%;
  padding: 1.5rem 0 0 0;
  letter-spacing: 1px;
}
section.about .about_pages .img-figure figcaption p {
  padding: 0 0.5rem;
  letter-spacing: 0px;
  opacity: 0;
  top: 50%;
  transform: translateY(40px);
}
section.about .about_pages .img-figure figcaption i {
  font-size: 20px;
  opacity: 0;
  transform: translateX(-10px);
}
section.about .about_pages .img-figure:hover img {
  zoom: 1;
  opacity: 0.5;
}
section.about .about_pages .img-figure:hover:after {
  opacity: 1;
  position: absolute;
  top: 10px;
  bottom: 10px;
  left: 10px;
  right: 10px;
}
section.about .about_pages .img-figure:hover h3,
section.about .about_pages .img-figure:hover p,
section.about .about_pages .img-figure:hover i {
  transform: translate(0px, 0px);
  opacity: 1;
}

/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Responsive Layout~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (max-width: 500px) {
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
  /* ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~About Section~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
  section.about .about_title {
    display: flex;
    flex-direction: column;
    width: 100%;
    text-align: center;
    position: relative;
  }
  section.about .about_title p {
    padding: 0 2rem 2rem;
    text-align: center;
    padding-bottom: 2rem;
  }
  section.about .about_pages .project {
    margin-bottom: 0 !important;
  }
  section.about .about_pages div {
    padding: 0 2rem 0;
    height: 50vh;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
  }
  section.about .about_pages .img-figure .icons {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    min-width: 200px;
    margin-bottom: 1rem;
  }
  section.about .about_pages .img-figure figcaption p {
    padding: 1rem 2.5rem;
    letter-spacing: 0px;
    opacity: 0;
    top: 50%;
    transform: translateY(40px);
  }
}
/* ========================================================================================= */
/* ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Tablet other sizes~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ */
@media (min-width: 599px) and (max-width: 960) {
  /*~~~~~~~~~~~~~~~~~~~~~~~~~ About Section~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
  section.about .about_pages div {
    height: 40vh !important;
  }
  section.about .about_pages .img-figure figcaption p {
    margin: 1rem 2.5rem;
    letter-spacing: 0px;
    opacity: 0;
    top: 50%;
    transform: translateY(40px);
  }
}
/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Normal  Screens~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (min-width: 769px) and (max-width: 1200px) {
  /*~~~~~~~~~~~~~~~~~~~~~~~~~ About Section~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
  section.about .container {
    height: 120vh;
    display: flex;
  }
  section.about .about_title {
    width: 50%;
    height: 75vh;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 !important;
  }
  section.about .about_pages {
    width: 50%;
  }
  section.about .about_pages .project {
    margin-bottom: 0;
  }
  section.about .about_pages div {
    height: 27vh;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
  }
  section.about .about_pages .img-figure .icons {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    min-width: 120px;
    margin-bottom: 1rem;
  }
  section.about .about_pages .img-figure:hover:after {
    opacity: 1;
    position: absolute;
    top: 15px;
    bottom: 15px;
    left: 15px;
    right: 15px;
  }
  section.about .about_pages .img-figure figcaption h3 {
    line-height: 1;
    opacity: 0;
    margin-bottom: 15px;
    width: 100%;
    padding: 2.5rem 0 0 0;
    letter-spacing: 1px;
  }
  section.about .about_pages .img-figure figcaption p {
    margin: 1rem 2.5rem;
    letter-spacing: 0px;
    opacity: 0;
    top: 50%;
    transform: translateY(40px);
  }
}
/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Widescreens~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (min-width: 1201px) {
  /*~~~~~~~~~~~~~~~~~~~~~~~~~ About Section~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
  section.about .container {
    height: 290vh;
    display: flex;
    /* position: relative; */
  }
  section.about .about_title {
    width: 50%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 !important;
  }
  section.about .about_pages {
    width: 50%;
    /* background-color: green; */
  }
  section.about .about_pages .project {
    margin-bottom: 0;
  }
  section.about .about_pages div {
    height: 70vh;
    display: flex;
    flex-direction: column;
    margin: 1rem 0;
    justify-content: space-evenly;
    align-items: center;
  }
  section.about .about_pages .img-figure .icons {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    min-width: 120px;
    margin-bottom: 1rem;
  }
  section.about .about_pages .img-figure:hover:after {
    opacity: 1;
    position: absolute;
    top: 15px;
    bottom: 15px;
    left: 15px;
    right: 15px;
  }
  section.about .about_pages .img-figure figcaption h3 {
    line-height: 1;
    opacity: 0;
    margin-bottom: 15px;
    width: 100%;
    padding: 3.5rem 0 0 0;
    letter-spacing: 1px;
  }
  section.about .about_pages .img-figure figcaption p {
    margin: 1rem 2.5rem;
    letter-spacing: 0px;
    opacity: 0;
    top: 50%;
    transform: translateY(40px);
  }
  section.about .vintage_corner_top {
    position: absolute;
    left: 0;
  }
}
</style>