<template>
  <v-app>
    <div
        v-if="isMobile()"
    >
      <v-system-bar color="blue darken-3"></v-system-bar>
      <v-app-bar
          color="info accent-4"
          dark
          prominent
      >
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>


        <v-spacer>
          Shop
        </v-spacer>
        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-filter</v-icon>
        </v-btn>
        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-app-bar>
      <v-navigation-drawer
          v-model="drawer"
          absolute
          bottom
          temporary
      >
        <v-list
            nav
            dense
        >
          <v-list-item-group
              v-model="group"
              active-class="deep-purple--text text--accent-4"
          >
            <v-list-item>
              <v-list-item-title>Foo</v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-title>Bar</v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-title>Fizz</v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-title>Buzz</v-list-item-title>
            </v-list-item>
          </v-list-item-group>
        </v-list>

      </v-navigation-drawer>

    </div>
    <div v-else>
      <b-navbar toggleable="lg" type="dark" variant="info">
        <b-navbar-brand href="#">NavBar</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item href="#">Delivery MEBEL</b-nav-item>
          </b-navbar-nav>

          <b-input-group class="mt-3 text-white">
            <template #prepend>
              <b-dropdown text="All" >
                <b-dropdown-item>Action A</b-dropdown-item>
                <b-dropdown-item>Action B</b-dropdown-item>
              </b-dropdown>
            </template>

            <b-form-input></b-form-input>
            <b-input-group-append>
              <b-button variant="warning">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-search"
                     viewBox="0 0 16 16">
                  <path
                      d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
                </svg>
              </b-button>
            </b-input-group-append>
          </b-input-group>
        </b-collapse>
        <b-navbar-nav>
          <b-nav-item>Account</b-nav-item>
          <b-nav-item>Orders</b-nav-item>
          <b-nav-item>Cart</b-nav-item>
        </b-navbar-nav>
      </b-navbar>
    </div>
    <v-main>
      <div v-if="isMobile()">
        <CAROUSEL_MOBILE />
      </div>
      <div v-else>
        <HelloWorld />
      </div>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import CAROUSEL_MOBILE from "./components/CAROUSEL_MOBILE";

export default {
  name: 'App',

  components: {
    CAROUSEL_MOBILE,
    HelloWorld,
  },

  data: () => ({
    drawer: false,
    group: null,
  }),
  methods: {
    isMobile() {
      if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
        return true
      } else {
        return false
      }
    }
  },
  watch: {
    group() {
      this.drawer = false
    },
  },
};
</script>
