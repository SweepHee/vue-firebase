<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" fixed app>
      <v-toolbar flat color='transparent'>
        <v-toolbar-title>Account</v-toolbar-title>
      </v-toolbar>
      <v-list>
        <v-list-group
        v-for="item in items"
        :key="item.title"
        v-model="item.active"
        :prepend-icon="item.icon"
        no-action
        >
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title v-text="item.title"></v-list-item-title>
          </v-list-item-content>
        </template>
        <v-list-item
          v-for="subItem in item.subItems"
          :key="subItem.title"
          :to="subItem.to"
        >
          <v-list-item-content>
            <v-list-item-title v-text="subItem.title"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>
  <v-card
    color="grey lighten-4"
    flat
    tile
  >
    <v-toolbar height="64px" dense color="green lighten-3">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Title</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>
  </v-card>

     <v-content>
        <router-view/>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  components: {

  },
  data () {
    return {
      drawer: false,
      items: [
        {
          icon: 'mdi-alert',
          title: 'home',
          active: true,
          subItems: [
            {
              title: 'dashboard',
              to: '/'
            },
            {
              title: 'About2',
              to: '/about'
            }
          ]
        },
        {
          icon: 'mdi-alert-box',
          title: 'Lectures',
          active: false,
          subItems: [
            {
              title: 'card',
              to: '/lectures/card'
            },
            {
              title: 'layout',
              to: '/lectures/layout'
            }
          ]
        }
      ]
    }
  },
  methods: {
  }
}
</script>
