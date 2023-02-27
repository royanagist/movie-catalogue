<!-- eslint-disable vue/multi-word-component-names -->
<script>
import { RouterLink } from "vue-router";
import SearchButton from "./SearchButton.vue";

export default {
  components: {
    SearchButton,
  },
};
</script>

<template>
  <nav class="navbar navbar-expand-lg">
    <div class="container-fluid">
      <a class="navbar-brand text-light" href="#">
        <img
          src="../../public/logo.png"
          alt="Logo"
          width="30"
          class="d-inline-block align-text-top"
        />
        Movie Catalogue
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <!-- <span class="navbar-toggler-icon"></span> -->
        <span class="" role="button"
          ><i class="fa fa-bars" aria-hidden="true" style="color: #e6e6ff"></i
        ></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <RouterLink class="nav-link text-light" to="/"> Movies </RouterLink>
          </li>
          <li class="nav-item">
            <RouterLink class="nav-link text-light" to="/tv"
              >TV Shows</RouterLink
            >
          </li>
          <li class="nav-item dropdown">
            <a
              class="nav-link dropdown-toggle text-light"
              href="#"
              role="button"
              data-bs-toggle="dropdown"
              aria-expanded="false"
            >
              Dropdown
            </a>
            <ul class="dropdown-menu">
              <li><a class="dropdown-item text-light" href="#">Action</a></li>
              <li>
                <a class="dropdown-item text-light" href="#">Another action</a>
              </li>
              <li><hr class="dropdown-divider" /></li>
              <li>
                <a class="dropdown-item text-light" href="#"
                  >Something else here</a
                >
              </li>
            </ul>
          </li>
        </ul>
        <form class="d-flex align-items-center" role="search">
          <div class="form-controls">
            <input type="value" required="" />
            <label>
              <span style="transition-delay: 0ms">F</span
              ><span style="transition-delay: 0ms">i</span
              ><span style="transition-delay: 50ms">n</span
              ><span style="transition-delay: 50ms">d</span
              ><span style="transition-delay: 100ms"></span
              ><span style="transition-delay: 100ms">M</span
              ><span style="transition-delay: 150ms">o</span
              ><span style="transition-delay: 150ms">v</span
              ><span style="transition-delay: 200ms">i</span
              ><span style="transition-delay: 200ms">e</span
              ><span style="transition-delay: 200ms">s</span>
            </label>
          </div>
          <SearchButton></SearchButton>
        </form>
      </div>
    </div>
  </nav>
</template>

<style scoped>
nav {
  background-color: rgba(var(--bg-dark-blue), 1);
  top: 10px;
}
.dropdown-menu {
  background-color: #0077b6;
}
.navbar-toggler-icon {
  color: white;
}

/* Search bar */
.form-controls {
  position: relative;
  margin: 10px;
  width: 190px;
}

.form-controls input {
  background-color: transparent;
  border: 0;
  border-bottom: 2px #fff solid;
  display: block;
  width: 100%;
  padding: 15px 0;
  font-size: 18px;
  color: #fff;
}

.form-controls input:focus,
.form-controls input:valid {
  outline: 0;
  border-bottom-color: lightblue;
}

.form-controls label {
  position: absolute;
  top: 15px;
  left: 0;
  pointer-events: none;
}

.form-controls label span {
  display: inline-block;
  font-size: 18px;
  min-width: 5px;
  color: #fff;
  -webkit-transition: 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
  transition: 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.form-controls input:focus + label span,
.form-controls input:valid + label span {
  color: lightblue;
  -webkit-transform: translateY(-30px);
  -ms-transform: translateY(-30px);
  transform: translateY(-30px);
}
button:active {
  -webkit-transform: scale(0.95);
  -ms-transform: scale(0.95);
  transform: scale(0.95);
}
</style>
