<template>
  <nav>
    <div class="logo">
      <img src="../assets/images/logo.svg" alt="" class="logo" />
    </div>

    <div class="burger" @click="toggleNav" :class="{ show: navIsOpen }">
      <div class="burger-icon"></div>
    </div>

    <div class="nav-links" :class="{ show: navIsOpen }">
      <ul class="main-links">
        <li>
          <a href="#">Features</a>
        </li>
        <li>
          <a href="#">Pricing</a>
        </li>
        <li>
          <a href="#">Resources</a>
        </li>
      </ul>
      <ul class="login-register">
        <li>
          <a href="#">Login</a>
        </li>
        <li>
          <a href="#" class="signup-btn">Signup</a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      navIsOpen: false,
    };
  },
  methods: {
    toggleNav() {
      this.navIsOpen = !this.navIsOpen;
    },
  },
};
</script>

<style>
nav {
  background-color: #fff;
  display: flex;
  align-items: center;
  padding: 15px 80px;
}

nav .logo {
  flex: 1 0 20%;
}

nav .nav-links {
  flex: 1 0 80%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

nav ul {
  display: flex;
  align-items: center;
  list-style: none;
  margin: 0;
  padding: 0;
}

nav ul li {
  margin: 0 10px;
}

nav ul li a {
  display: inline-block;
  color: hsl(0, 0%, 75%);
  text-decoration: none;
}

nav .signup-btn {
  background-color: hsl(180, 66%, 49%);
  border-radius: 30px;
  color: #fff;
	padding: 8px 0;
	width: 140px;
	text-align: center;
}

nav .burger {
  position: relative;
  display: none;
  justify-content: center;
  align-items: center;
  height: 40px;
  width: 40px;
  cursor: pointer;
  transition: all 0.5s ease-in-out;
  border: 3px solid #fff;
}

nav .burger .burger-icon {
  width: 30px;
  height: 3px;
  background-color: hsl(0, 0%, 75%);
  border-radius: 5px;
  transition: all 0.5s ease-in-out;
}

nav .burger .burger-icon::before,
nav .burger .burger-icon::after {
  position: absolute;
  content: "";
  width: 30px;
  height: 3px;
  background-color: hsl(0, 0%, 75%);
  border-radius: 5px;
  transition: all 0.5s ease-in-out;
}

nav .burger .burger-icon::before {
  transform: translateY(-8px);
}

nav .burger .burger-icon::after {
  transform: translateY(8px);
}

nav .burger.show .burger-icon {
  transform: translateX(-50px);
  background-color: transparent;
}

nav .burger.show .burger-icon::before {
  transform: rotate(45deg) translate(35px, -35px);
}

nav .burger.show .burger-icon::after {
  transform: rotate(-45deg) translate(35px, 35px);
}

@media screen and (max-width: 768px) {
  nav {
    padding: 30px 20px 15px;
    align-items: flex-start;
  }

  nav .nav-links {
    background-color: hsl(257, 27%, 26%);
    box-shadow: 0 3px 5px rgba(0, 0, 0, 0.1);
    position: fixed;
    top: 75px;
    left: 5%;
    width: 90%;
    flex-direction: column;
    text-align: center;
    border-radius: 10px;
    padding: 20px;
    transform: translateX(120%);
    transition: transform 0.4s ease-in-out;
    z-index: 9999;
  }

  nav .nav-links.show {
    transform: translateX(0);
  }

  nav .nav-links ul {
		width: 100%;
    flex-direction: column;
  }

  nav .nav-links ul li {
    margin: 15px;
  }

  nav .nav-links ul li a {
    color: #fff;
  }

  nav .nav-links .main-links {
		margin-bottom: 14px;
		padding-bottom:14px;
    border-bottom: 1px solid hsl(0, 0%, 75%);
  }

  nav .burger {
		transform: translateY(-6px);
    display: flex;
  }
}
</style>