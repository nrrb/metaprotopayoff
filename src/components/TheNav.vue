<template>
  <div>
    <v-navigation-drawer
      class="primary"
      v-model="drawer"
      app
      dark
    >
      <v-list>
          <v-list-item
            v-for="link in linksInternal"
            :key="link.text"
            :to="link.route"
            exact
          >
            <v-list-item-icon>
              <v-icon v-text="link.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="link.text"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
      </v-list>
      <v-list
        v-if="isPresentationDay"
      >
          <v-list-item
            v-for="link in linksExternal"
            :key="link.text"
            :href="link.href"
            exact
          >
            <v-list-item-icon>
              <v-icon v-text="link.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="link.text"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
    </v-navigation-drawer>

    <v-app-bar color="primary" dark app>
      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <v-toolbar-title>{{ appTitle }}</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        href="https://github.com/lovingawareness/metaprotopayoff"
        target="_blank"
      >
        <v-icon
          left
        >
          mdi-github
        </v-icon>
        this site's code
      </v-btn>
      
    </v-app-bar>
  </div>
</template>

<script>
import Vue from "vue"
import moment from "moment"

export default Vue.extend({
  name: "TheNav",
  data() {
    return {
      appTitle: 'Meta - Kellogg Proto Payoff Simulation',
      drawer: false,
      linksExternal: [
        {
          text: "Demo - Player",
          icon: "mdi-controller-classic-outline",
          href: "https://payoff.sim.kellogg.northwestern.edu/"
        },
        {
          text: "Demo - Admin",
          icon: "mdi-head-minus-outline",
          href: "https://payoff.sim.kellogg.northwestern.edu/9KQ6P/"
        }
      ],
      linksInternal: [
        {
          text: "Home",
          icon: "mdi-home",
          route: "/"
        },
        {
          text: "Technical Background",
          icon: "mdi-book-open-page-variant-outline",
          route: "/background"
        },
        {
          text: "How The App Is Made",
          icon: "mdi-hammer-wrench",
          route: "/howitsmade"
        },
        {
            text: "Learning Resources",
            icon: "mdi-school-outline",
            route: "/learning"
        },
        {
          text: "About This Site",
          icon: "mdi-information-outline",
          route: "/about"
        }
      ]
    }
  },
  computed: {
    isPresentationDay() {
      return moment().diff(moment('2021-06-25')) < 0
    }
  }
})
</script>

<style scoped>
header {
  /* position: absolute !important; */
  top: 0 !important;
  left: 0 !important;
  z-index: 99999 !important;
}

nav,
main {
  margin-top: 4rem !important;
}

main {
  padding: 2rem;
}
</style>