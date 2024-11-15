<template>
    <div>
      <nav class="navbar fixed-top bg-dark navbar-expand-lg bg-body-tertiary" data-bs-theme="dark">
        <div class="container-fluid">
          <router-link class="navbar-brand" to="/">MyTube</router-link>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
            aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNav" @mouseenter="handleMouseEnter"
            @mouseleave="handleMouseLeave">
            <ul class="navbar-nav">
              <li class="nav-item">
                <router-link class="nav-link" to="/">Home</router-link>
              </li>
              <li class="nav-item">
                <router-link class="nav-link" to="/search">Search</router-link>
              </li>
              <li class="nav-item">
                <router-link class="nav-link" to="/later">Later</router-link>
              </li>
            </ul>
          </div>
        </div>
      </nav>
    </div>
  </template>
  
  <script>
  export default {
    methods: {
      handleMouseEnter() {
        const navbarNav = document.getElementById('navbarNav');
        if (!navbarNav.classList.contains('show')) {
          const collapse = new bootstrap.Collapse(navbarNav, {
            toggle: true
          });
          collapse.show();
        }
      },
      handleMouseLeave() {
        const navbarNav = document.getElementById('navbarNav');
        if (navbarNav.classList.contains('show')) {
          const collapse = new bootstrap.Collapse(navbarNav, {
            toggle: true
          });
          collapse.hide();
        }
      }
    }
  };
  </script>
  