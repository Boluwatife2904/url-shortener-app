<template>
  <footer>
    <div class="logo-area">
      <img src="../assets/images/logo.svg" alt="" />
    </div>
    <div class="footer-area">
      <h4>Features</h4>
      <ul>
        <li>
          <a href="#">Link Shortening</a>
        </li>
        <li>
          <a href="#">Branded Links</a>
        </li>
        <li>
          <a href="#">Analytics</a>
        </li>
      </ul>
    </div>
    <div class="footer-area">
      <h4>Resources</h4>
      <ul>
        <li>
          <a href="#">Blog</a>
        </li>
        <li>
          <a href="#">Developers</a>
        </li>
        <li>
          <a href="#">Support</a>
        </li>
      </ul>
    </div>
    <div class="footer-area">
      <h4>Company</h4>
      <ul>
        <li>
          <a href="#">About</a>
        </li>
        <li>
          <a href="#">Our Team</a>
        </li>
        <li>
          <a href="#">Careers</a>
        </li>
        <li>
          <a href="#">Contact</a>
        </li>
      </ul>
    </div>
    <div class="social-media-area">
      <ul>
        <li>
          <a href="#"><i class="fab fa-facebook-square"></i></a>
        </li>
        <li>
          <a href="#"><i class="fab fa-twitter"></i></a>
        </li>
        <li>
          <a href="#"><i class="fab fa-pinterest"></i></a>
        </li>
        <li>
          <a href="#"><i class="fab fa-instagram"></i></a>
        </li>
      </ul>
    </div>
  </footer>
</template>

<script>
export default {
  name: "TheFooter",
};
</script>

<style>
footer {
  padding: 60px 80px;
  background: hsl(260, 8%, 14%);
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  overflow: hidden;
}

footer img {
  filter: invert(1);
}

footer .logo-area {
  flex: 1 0 28%;
  margin-bottom: 30px;
}

footer .footer-area,
footer .social-media-area {
  flex: 1 0 18%;
  margin-bottom: 20px;
}

footer .footer-area h4 {
  color: #fff;
  margin-bottom: 20px;
  font-weight: 600;
  font-size: 18px;
}

footer .footer-area ul,
footer .social-media-area ul {
  list-style: none;
}

footer .footer-area ul li {
  display: block;
  margin-bottom: 12px;
}

footer .footer-area ul li a,
footer .social-media-area ul li a {
  display: inline-block;
  color: hsl(0, 0%, 75%);
  text-decoration: none;
  outline: none;
  font-size: 16px;
  transition: all 0.4s ease-in-out;
}

footer .footer-area ul li a:hover,
footer .social-media-area ul li a:hover {
  color: hsl(180, 66%, 49%);
}

footer .social-media-area ul {
  display: flex;
}

footer .social-media-area ul li {
  margin-right: 15px;
}

footer .social-media-area ul li a {
  color: #ffffff;
  font-size: 22px;
}

@media screen and (max-width: 992px) {
   footer .social-media-area ul {
    justify-content: center;
  }
}

@media screen and (max-width: 768px) {
  footer{
    padding: 60px 40px;
  }

  footer .logo-area {
    flex: 1 0 100%;
  }

  footer .footer-area{
    flex: 1 0 33.3%;
  }

  footer .social-media-area {
    flex: 1 0 100%;
  }

  footer .social-media-area ul {
    justify-content: center;
  }
}

@media screen and (max-width: 576px) {
  footer .logo-area {
    flex: 1 0 100%;
  }

  footer .footer-area,
  footer .social-media-area {
    flex: 1 0 50%;
  }

  footer .social-media-area ul {
    justify-content: flex-start !important;
  }
}

@media screen and (max-width: 440px) {
  footer {
    padding: 60px 20px;
  }

  footer .logo-area {
    flex: 1 0 100%;
  }

  footer .logo-area img{
    display: block;
    margin: 0 auto;
  }

  footer .footer-area,
  footer .social-media-area {
    flex: 1 0 100%;
    text-align: center;
  }

  footer .social-media-area ul{
    justify-content: center !important;
    margin: 0 auto;
  }
}
</style>