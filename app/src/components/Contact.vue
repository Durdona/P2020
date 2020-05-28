<template>
  <div>
    <section id="contact-me">
      <div class="container">
        <div class="section-title">
          <h2>Get In Touch</h2>
          <p class="contactSub">...........................................................</p>
        </div>

        <div class="section-content">
          <div id="contact-anim-icons">
            <div class="anim-text">
              <div>Creative Developer</div>
              <div>JavaScript Lover</div>
              <div>Lifelong Learner</div>
              <div>Positive Attitude</div>
              <div>Passionate about</div>
              <div>Constant Growth</div>
              <div>Embraces Challenges</div>
            </div>
            <div class="hover-anim-text">
              <div>Creative Developer</div>
              <div>JavaScript Lover</div>
              <div>Lifelong Learner</div>
              <div>Positive Attitude</div>
              <div>Passionate about</div>
              <div>Constant Growth</div>
              <div>Embraces Challenges</div>
            </div>
            <div class="contact-icons-container">
              <div class="contact-me-icons">
                <a href="tel:+717-742-0772">
                  <!-- <i class="fas fa-mobile-alt"></i> -->
                  <i class="fas fa-phone-alt"></i>
                </a>
                <h3>Phone</h3>
                <p class="phone-text">(717) 742-0772</p>
              </div>
              <div class="contact-me-icons">
                <a href="mailto:code4hacking@gmail.com">
                  <i class="far fa-envelope"></i>
                </a>
                <h3>Email</h3>
                <p class="email-text">code4hacking@</p>
              </div>

              <div class="contact-me-icons">
                <a href="https://www.google.com/maps/place/Pittsburgh,+PA" target="_blank">
                  <i class="fas fa-globe-americas"></i>
                </a>
                <h3>Address</h3>
                <p class="address-text">Pittsburgh, PA</p>
              </div>
            </div>
          </div>
          <div id="contact-form">
            <div class="top_ornament_vintage">
              <img src="../assets/img/top_form_ornament.svg" alt />
            </div>
            <form name="contact" method="POST" data-netlify="true" data-netlify-recaptcha="true">
              <p class="text-field text-name">
                <input
                  type="text"
                  class="text-input name-input"
                  placeholder="Name"
                  name="name"
                  required
                />
                <label for="name">
                  <i class="far fa-user name-icon"></i>
                </label>
              </p>
              <p class="text-field text-subject">
                <input
                  type="text"
                  class="text-input subject-input"
                  placeholder="Subject"
                  name="subject"
                />
                <label for="subject">
                  <i class="far fa-comment subject-icon"></i>
                </label>
              </p>
              <p class="text-field text-email">
                <input
                  type="email"
                  class="text-input email-input"
                  placeholder="Email"
                  name="email"
                  required
                />
                <label for="email">
                  <i class="far fa-envelope email-icon"></i>
                </label>
              </p>
              <p class="text-field text-phone">
                <input
                  type="text"
                  class="text-input phone-input"
                  placeholder="Phone Number"
                  name="phone"
                />
                <label for="phone">
                  <i class="fas fa-phone-alt phone-icon"></i>
                </label>
              </p>
              <p class="text-field text-message">
                <textarea
                  type="text"
                  class="text-input message-input"
                  placeholder="Enter Message"
                  name="message"
                  required
                ></textarea>
                <label for="message">
                  <i class="fas fa-feather-alt message-icon"></i>
                </label>
              </p>
              <div class="my-recaptcha">
                <div data-netlify-recaptcha="true"></div>
              </div>
              <button type="submit" class="button">Submit</button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <section id="contact-footer">
      <div class="container">
        <h3>Let's Start Your Next Project</h3>
      </div>
    </section>
  </div>
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
  name: "Contact",
  methods: {
    contactMe() {
      // Contact Header w/ its paragraph, Form and its Top Ornament Animation on Scrolling ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
      const formController = new ScrollMagic.Controller(); // one controller will be used for all 4 HTML elements
      // `````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````
      // Contact Me h2 Header Animation on Scrolling Event
      let contactHeaderTl = gsap.timeline();
      contactHeaderTl.from(".section-title h2", {
        duration: 1,
        scale: 0.5,
        stagger: 0.8,
        opacity: 0,
        transformOrigin: "50% 50%"
      });
      // Scene for Header h2
      new ScrollMagic.Scene({
        triggerElement: ".section-title h2",
        triggerHook: 0.9
      })
        .setTween(contactHeaderTl)
        .addTo(formController);

      // `````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````
      //Adding Typing Effect for subheader Paragraph on Scrolling Event
      let contactSubTL = gsap.timeline();
      function contactSubHeaderAnim() {
        contactSubTL.addPause(4).to(
          ".contactSub",
          {
            ease: "sine.out",
            duration: 4,
            color: "bisque",
            text: "Here is how you can reach me",
            stagger: 1
          },
          "-=3"
        );
      }
      // scene for Sub Paragraph Header Typing Effect
      new ScrollMagic.Scene({
        triggerElement: ".contactSub",
        triggerHook: 0.6
      })
        .setTween(contactSubTL)
        .addTo(formController);
      contactSubHeaderAnim(); // without using function I was getting warning in the console !

      // `````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````
      // Scene (Scrolling Event) for Animating Form without gsap timeline ... used .setClassToggle to trigger ".fade-in" class (check CSS file)
      new ScrollMagic.Scene({
        // scene for form itself
        triggerElement: "#contact-form",
        triggerHook: 0.7
      })
        .setClassToggle("#contact-form", "fade-in")
        .addTo(formController);

      // `````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````
      // New Scrolling Event for Top Form Ornament
      let ornamentTl = gsap.timeline();
      ornamentTl.from(".top_ornament_vintage", {
        duration: 1,
        scale: 0,
        stagger: 0.5,
        opacity: 0,
        transformOrigin: "50% 50%"
      });
      // Scene for Form Top Ornament
      new ScrollMagic.Scene({
        triggerElement: ".top_ornament_vintage",
        triggerHook: 0.8
      })
        .setTween(ornamentTl)
        .addTo(formController);

      // Contact Me Footer Header  on Scrolling Event ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
      let contactMeFooterHeaderTl = gsap.timeline();
      gsap.set("#contact-footer h3 ", { autoAlpha: 1 });
      contactMeFooterHeaderTl.from("#contact-footer h3", {
        duration: 1,
        opacity: 0,
        scale: 0,
        rotation: 180,
        transformOrigin: "50% 50%"
      });
      // Scene for Contact Me Footer Header
      new ScrollMagic.Scene({
        triggerElement: "#contact-footer h3",
        triggerHook: 1
      })
        .setTween(contactMeFooterHeaderTl)
        .addTo(formController);
      // ===============================================================================================
      // Rollover Text Animation of Contact Form on Scrolling Event ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
      let animText = gsap.timeline();
      gsap.set("#contact-anim-icons ", { autoAlpha: 1 });
      animText
        .from("#contact-anim-icons .anim-text div", {
          y: 80,
          opacity: 0,
          stagger: 1,
          duration: 1.5
        })
        .to(
          "#contact-anim-icons .anim-text div",
          { y: -80, opacity: 0, stagger: 1, duration: 1.5 },
          1
        );
      new ScrollMagic.Scene({
        triggerElement: "#contact-anim-icons .anim-text div",
        triggerHook: 0.5
      })
        .setTween(animText)
        .addTo(formController);
      // .addIndicators()

      // ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
      // Rollover Text Animation on hovering Email Icon ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
      document
        .querySelector(".contact-me-icons .fa-envelope")
        .addEventListener("mouseover", function() {
          let hover_anim_text = gsap.timeline();
          gsap.set("#contact-anim-icons .hover-anim-text", { autoAlpha: 1 });
          hover_anim_text
            .from("#contact-anim-icons .hover-anim-text div", {
              y: 80,
              opacity: 0,
              stagger: 1,
              duration: 1.5
            })
            .to(
              "#contact-anim-icons .hover-anim-text div",
              { y: -80, opacity: 0, stagger: 1, duration: 1.5 },
              1
            );
        });

      // ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
      // Contact Me Icons Animation on Hover Event~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
      document
        .querySelector(".fa-phone-alt")
        .addEventListener("mouseover", function() {
          let phoneIcontl = gsap.timeline();
          phoneIcontl
            .from(".phone-text", {
              duration: 0.5,
              scale: 0.5,
              transformOrigin: "50% 50%",
              stagger: 0.5,
              opacity: 0
            })
            .from(".fa-phone-alt", {
              duration: 0.1,
              opacity: 0.5,
              ease: "power2.out"
            });
        });

      document
        .querySelector(".fa-envelope")
        .addEventListener("mouseover", () => {
          let emailIcontl = gsap.timeline();
          emailIcontl
            .from(".email-text", {
              duration: 0.5,
              scale: 0.5,
              transformOrigin: "50% 50%",
              stagger: 0.5,
              opacity: 0
            })
            .from(".fa-envelope", {
              duration: 0.1,
              opacity: 0.5,
              ease: "power2.out"
            });
        });

      document
        .querySelector(".fa-globe-americas")
        .addEventListener("mouseover", () => {
          let emailIcontl = gsap.timeline();
          emailIcontl
            .from(".address-text", {
              duration: 0.5,
              scale: 0.5,
              transformOrigin: "50% 50%",
              stagger: 0.5,
              opacity: 0
            })
            .from(".fa-globe-americas", {
              duration: 0.1,
              opacity: 0.5,
              ease: "power2.out"
            });
        });
    }
  },
  mounted: function() {
    this.contactMe();
  }
};
</script>

<style>
/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Contact Me Section~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
.section-content {
  width: 100% !important;
}
#contact-me {
  background: linear-gradient(to bottom left, #0a051c, rgba(2, 4, 41, 1));
  padding-bottom: 2rem;
  height: 100%;
  width: 100%;
}
#contact-me .top_ornament_vintage {
  width: 100%;
  padding-bottom: 2rem;
}
#contact-me .top_ornament_vintage img {
  width: 80%;
  display: block;
  margin: 0 auto;
}
#contact-me .section-title {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
#contact-me .section-title h2 {
  padding-top: 2rem;
}
#contact-me .section-title p {
  padding-top: 1rem;
}
#contact-me .container .section-content {
  display: flex;
  justify-content: space-between;
  position: relative;
}
#contact-anim-icons {
  visibility: hidden;
  width: 50%;
}
#contact-anim-icons .anim-text div {
  position: absolute;
  display: inline-block;
  left: 25%;
  top: 10%;
  font-size: 3rem;
  transform: translate(-50%, -50%);
  white-space: nowrap;
  letter-spacing: 0;
}
#contact-anim-icons .hover-anim-text {
  visibility: hidden;
}
#contact-anim-icons .hover-anim-text div {
  position: absolute;
  display: inline-block;
  left: 25%;
  top: 20%;
  font-size: 3rem;
  transform: translate(-50%, -50%);
  white-space: nowrap;
  letter-spacing: 0;
}
.contact-icons-container {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  height: 100%;
  align-items: center;
  text-align: center;
}
.contact-me-icons {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.contact-me-icons h3 {
  font-size: 1.9rem;
}
.contact-me-icons .fa-envelope,
.contact-me-icons .fa-phone-alt,
.contact-me-icons .fa-globe-americas {
  font-size: 2.2rem;
  padding: 10px;
}
.contact-me-icons .fa-envelope:hover,
.contact-me-icons .fa-phone-alt:hover,
.contact-me-icons .fa-globe-americas:hover {
  color: rgb(240, 230, 140);
  cursor: pointer;
  transition: all 0.2s ease;
}
#contact-form {
  width: 36%;
  padding-right: 1rem;
  opacity: 0;
  transform: translateY(100px);
  transition: all 1s ease-out;
}
#contact-form.fade-in {
  opacity: 1;
  transform: translateY(0);
}
#contact-form .text-field {
  width: 100%;
  display: flex;
  padding: 0 1rem;
}
#contact-form .text-input {
  font-family: inherit;
  letter-spacing: 1px;
  font-size: 1.2rem;
  color: bisque;
  margin-bottom: 2rem;
  flex: 1;
  padding: 1.2rem;
  background: linear-gradient(
    to bottom right,
    rgba(2, 4, 41, 0.1),
    rgba(10, 1, 30, 1)
  );
  border: none;
  padding-left: 2.9rem;
  border-radius: 5px;
  border-bottom: 1px solid bisque;
  border-right: 1px solid bisque;
  border-top: 1px solid #000;
  border-left: 1px solid #000;
}
#contact-form .text-field textarea {
  resize: vertical;
  width: 100%;
  height: 10rem;
}
.text-name,
.text-subject,
.text-email,
.text-phone,
.text-message {
  position: relative;
}
.name-icon,
.subject-icon,
.email-icon,
.phone-icon {
  position: absolute;
  left: 30px;
  top: calc(50% - 1.1em);
  color: rgba(255, 228, 196, 0.7);
}
.message-icon {
  position: absolute;
  left: 30px;
  top: calc(50% - 3em);
  color: rgba(255, 228, 196, 0.7);
}
#contact-form .name-input:focus-within,
#contact-form .subject-input:focus-within,
#contact-form .email-input:focus-within,
#contact-form .phone-input:focus-within,
#contact-form .message-input:focus-within {
  background: linear-gradient(
    to bottom left,
    rgba(40, 1, 40, 0.5),
    rgba(2, 4, 41, 1)
  );
  color: goldenrod;
  font-size: 1.2rem;
  border: 1px solid #000;
  border-top: 1px solid bisque;
  border-left: 1px solid bisque;
}
#contact-form button {
  width: 10rem;
  font-size: 1.2rem;
  float: right;
  margin-right: 15px;
}
#contact-form button {
  background: url("../assets/img/vintage_hover.svg") no-repeat center
    center/cover;
  color: black;
  font-weight: bold;
}
#contact-form button:hover {
  background: url("../assets/img/vintage.svg") no-repeat center center/cover;
  color: bisque;
}
#contact-footer {
  /* background: linear-gradient(to bottom left, rgba(2, 4, 41, 1), rgba(2, 4, 41, 0.02)); */
  background: linear-gradient(
    to bottom left,
    rgba(2, 4, 41, 1),
    rgba(40, 1, 40, 0.3)
  );
  width: 100%;
}
#contact-footer .container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
#contact-footer h3 {
  visibility: hidden;
  padding: 3rem 0;
}

/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Responsive Layout~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/

/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Smartphones ~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (max-width: 500px) {
  #contact-me .container .section-content {
    display: inline-block;
  }
  .anim-text,
  .hover-anim-text {
    display: none;
  }
  .contact-icons-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    /* padding-right: 2rem; */
  }
  #contact-anim-icons {
    width: 100%;
  }
  #contact-form {
    width: 100%;
    padding-right: 0;
  }
  #contact-footer h3 {
    font-size: 1.4rem;
  }
}

/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Tablets~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (min-width: 501px) and (max-width: 768px) {
  #contact-me .container .section-content {
    display: inline-block;
  }
  .anim-text,
  .hover-anim-text {
    display: none;
  }
  .contact-icons-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  #contact-anim-icons {
    width: 100%;
  }
  #contact-form {
    width: 100%;
    padding-right: 0;
    padding: 0 2rem;
  }
  #contact-footer h3 {
    font-size: 1.4rem;
  }
}
/* ========================================================================================= */
/* ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Tablet other sizes~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ */
@media (min-width: 599px) and (max-width: 960) {
  #contact-me .container .section-content {
    display: inline-block;
  }
  .anim-text,
  .hover-anim-text {
    display: none;
  }
  .contact-icons-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    /* padding-right: 2rem; */
  }
  #contact-anim-icons {
    width: 100%;
  }
  #contact-form {
    width: 100%;
    padding-right: 0;
    padding: 0 2rem;
  }
  #contact-footer h3 {
    font-size: 1.4rem;
  }
}
/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Normal  Screens~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (min-width: 769px) and (max-width: 1200px) {
  #contact-me .container .section-content {
    display: inline-block;
  }
  .anim-text,
  .hover-anim-text {
    display: none;
  }
  .contact-icons-container {
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    text-align: center;
    /* padding-right: 2rem; */
  }
  #contact-anim-icons {
    width: 100%;
  }
  #contact-form {
    width: 100%;
    padding-right: 0;
    padding: 0 5rem;
  }
  #contact-footer h3 {
    font-size: 1.4rem;
  }
}

/* ========================================================================================= */
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Widescreens~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (min-width: 1201px) {
}
</style>