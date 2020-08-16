<template>
  <div id="my-nav">
    <b-navbar toggleable="lg" type="dark" variant="dark" fixed="top">
      <b-navbar-brand to="/">NavBar</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="/">Home</b-nav-item>
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto" v-show="logged">
          <b-nav-item-dropdown text="Lang" right>
            <b-dropdown-item href="#">EN</b-dropdown-item>
            <b-dropdown-item href="#">ES</b-dropdown-item>
            <b-dropdown-item href="#">RU</b-dropdown-item>
            <b-dropdown-item href="#">FA</b-dropdown-item>
          </b-nav-item-dropdown>

          <b-nav-item-dropdown right>
            <!-- Using 'button-content' slot -->
            <template v-slot:button-content>
              <em>User</em>
            </template>
            <b-dropdown-item href="#">Profile</b-dropdown-item>
            <b-dropdown-item href="#">Sign Out</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
        <b-navbar-nav class="ml-auto" v-show="!logged">
          <b-nav-item-dropdown text="Lang" right>
            <b-dropdown-item href="#">EN</b-dropdown-item>
            <b-dropdown-item href="#">ES</b-dropdown-item>
            <b-dropdown-item href="#">RU</b-dropdown-item>
            <b-dropdown-item href="#">FA</b-dropdown-item>
          </b-nav-item-dropdown>

          <b-nav-item to="/register">Sign Up</b-nav-item>
          <b-nav-item to="login">Sign In</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
  import 
  {
    BNavbar,
    BNavbarNav,
    BNavbarBrand,
    BNavbarToggle,
    BCollapse,
    BNavItem,
    BNavItemDropdown,
    BDropdownItem
  } from 'bootstrap-vue'

  export default {
    name: 'Navbar',
    components: {
      BNavbar,
      BNavbarNav,
      BNavbarBrand,
      BNavbarToggle,
      BCollapse,
      BNavItem,
      BNavItemDropdown,
      BDropdownItem
    },
    data() {
      return {
        logged: false
      }
    },
    methods: {
      sign_out() {
        this.logged = false;
      }
    },
  }
</script>

<style lang="css" scoped>
  #my-nav {
  padding: 30px;
}

#my-nav a {
  font-weight: bold;
}

#my-nav a.router-link-exact-active {
  color: #42b983;
}
</style>