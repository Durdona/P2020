<template>
  <div>
    <footer id="main-footer">
      <div class="footer-content container">
        <p>Copyright © 2020. All Rights Reserved</p>
        <div class="social">
          <a href="https://twitter.com/Abdusamikovna" target="_blank">
            <i class="fab fa-twitter"></i>
          </a>
          <a href="https://www.facebook.com/durdona.abdusamikovna" target="_blank">
            <i class="fab fa-facebook-f"></i>
          </a>
          <a href="https://stackoverflow.com/users/4930023/durdona-abdusamikovna?tab=topactivity">
            <i class="fab fa-stack-overflow" target="_blank"></i>
          </a>
          <a href="https://github.com/Durdona" target="_blank">
            <i class="fab fa-github"></i>
          </a>
        </div>
      </div>
      <div class="vintage_corner_right">
        <img src="../assets/img/vintage_corner_right.svg" alt="corner" />
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "Footer"
};
</script>

<style>
footer {
  height: 12vh;
  background: linear-gradient(
    to bottom left,
    rgba(2, 4, 41, 1),
    rgba(40, 1, 40, 0.3)
  );
  /* background: linear-gradient(
    to bottom left,
    rgba(2, 4, 41, 1),
    rgba(2, 4, 41, 0.02)
  ); */
  position: relative;
}
.vintage_corner_right {
  position: absolute;
  bottom: 0;
  right: 3%;
}
div.footer-content {
  padding-left: 2rem;
  padding-bottom: 0.5rem;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: flex-end;
  height: 100%;
}
.footer-content p {
  font-size: 1rem;
  letter-spacing: 1px;
}
.footer-content .social {
  padding-bottom: 1.4rem;
  display: flex;
  width: 140px;
  justify-content: space-around;
  align-items: center;
}
.footer-content .social i {
  font-size: 1.2rem;
}
.footer-content .social i:nth-child(1) {
  padding-left: 20px;
}
.footer-content .social .fa-twitter:hover {
  color: #1d9cec;
}
.footer-content .social .fa-facebook-f:hover {
  color: #1d4595;
}
.footer-content .social .fa-stack-overflow:hover {
  color: #ed7d23;
}
.footer-content .social .fa-github:hover {
  color: palegoldenrod;
}
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Responsive Layout~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/

/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Smartphones ~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (max-width: 500px) {
  div.footer-content {
    padding-left: 1rem;
    /* padding-bottom: 1rem; */
  }
  div.footer-content p {
    padding-bottom: 1rem;
    padding-top: 1rem;
    letter-spacing: 1px;
  }
  .footer-content .social {
    width: 220px;
  }
  .vintage_corner_right {
    display: none;
  }
}
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ Tablets~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (min-width: 501px) and (max-width: 768px) {
  div.footer-content {
    padding-left: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
  }
  div.footer-content p {
    padding-bottom: 1rem;
    padding-top: 1.5rem;
    letter-spacing: 1px;
  }
  .footer-content .social {
    width: 150px;
    padding-bottom: 0.75rem;
  }
  .footer-content .social i:nth-child(1) {
    padding-left: 0;
  }
}
/* ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Tablet other sizes~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ */
@media (min-width: 599px) and (max-width: 960) {
  div.footer-content {
    padding-left: 1rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
  }
  div.footer-content p {
    padding-bottom: 1rem;
    padding-top: 1.5rem;
    letter-spacing: 1px;
  }
  .footer-content .social {
    width: 150px;
    padding-bottom: 0.75rem;
  }
  .footer-content .social i:nth-child(1) {
    padding-left: 0;
  }
}
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Normal  Screens~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
@media (min-width: 769px) and (max-width: 1200px) {
  div.footer-content {
    padding-left: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: flex-start;
  }
  div.footer-content p {
    padding-bottom: 1rem;
    padding-top: 1.5rem;
    letter-spacing: 1px;
  }
  .footer-content .social {
    width: 150px;
    padding-bottom: 0.75rem;
  }
  .footer-content .social i:nth-child(1) {
    padding-left: 0;
  }
}
@media (min-width: 1201px) {
  .vintage_corner_right {
    position: absolute;
    bottom: 0;
    right: 1.2%;
  }
}
</style>