<template>
  <div id="app">
    <Home />
    <About />
    <Contact />
    <Footer />
  </div>
</template>

<script>
import Home from "./components/Home";
import About from "./components/About";
import Contact from "./components/Contact";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    Home,
    About,
    Contact,
    Footer
  },
  mounted: function() {
    console.clear();
    if (typeof console === "object") {
      console.log(
        "\n" +
          "===============================================\n" +
          "Hi there, fellow developer! Thanks for visiting.\n" +
          "===============================================\n" +
          "                                        Durdona\n"
      );
    }
  }
};
</script>

<style>
@import url("../node_modules/@fortawesome/fontawesome-free/css/all.min.css");
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@200&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
html {
  width: 100vw;
  overflow-x: hidden;
}

html,
body {
  font-family: "Montserrat", sans-serif;
  letter-spacing: 0.5px;
  font-size: 1rem;
  line-height: 1.4;
  background-color: rgba(2, 4, 41, 0.8);
  color: bisque;
}
a {
  text-decoration: none;
  color: bisque;
}
h1 {
  font-size: 3.4rem;
  padding-bottom: 1rem;
  font-weight: lighter;
}
h2 {
  font-size: 2.8rem;
  font-weight: lighter;
  padding: 1rem 0;
}
h3 {
  font-size: 2rem;
  font-weight: lighter;
  padding-bottom: 1rem;
}
p {
  font-size: 1.4rem;
  padding-bottom: 1.2rem;
}
/* Container */
.container {
  padding: 0 1rem;
  padding-right: 2rem;
  margin: auto;
  overflow: hidden;
}
/* Button */
.button {
  background: url("./assets/img/vintage.svg") no-repeat center center/cover;
  padding: 30px;
  font-size: 1.2rem;
}
.button:hover {
  background: url("./assets/img/vintage_hover.svg") no-repeat center
    center/cover;
  color: black;
  font-weight: bold;
  transition: all 0.6s ease;
  cursor: pointer;
}
button {
  font-family: inherit;
  color: bisque;
  padding: none;
  border: none;
  outline: none;
}
/* Input fields */
input,
textarea {
  outline: none;
}
input::placeholder,
textarea::placeholder {
  font-size: 1.2rem;
  color: rgba(255, 255, 255, 0.5);
}
input:focus,
textarea:focus {
  outline: none;
  padding-left: 60px;
  transition: all 0.6s ease;
}
</style>
