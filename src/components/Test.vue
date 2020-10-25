<template>
  <nav>
    <v-app-bar color="blue accent-3" dark app>

      <v-app-bar-nav-icon @click.stop="drawer = !drawer">

      </v-app-bar-nav-icon>

      <v-toolbar-title class="text-uppercase">
        <span class="font-weight-light">TooMany</span>
        <span>Class</span>
      </v-toolbar-title>

      <v-spacer></v-spacer>
<!-- MENU -->
      <v-menu offset-y>
        <template v-slot:activator="{ on }">
          <v-btn text v-on="on">
            <v-icon left>
              expand_more
            </v-icon>
            <span>Menu</span>
          </v-btn>
        </template>
        <v-list flat>
          <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
            <v-list-item-title>{{link.text}}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
<!-- MENU -->
    </v-app-bar>

      <!-- MENU LATERAL -->
      <v-navigation-drawer v-model="drawer" dark app class="blue accent-3">

      <v-layout column align-center>
        <v-flex class="mt-5">
          <v-avatar size="100" class="mb-4">
            <v-img src="/perfil.png"/>
          </v-avatar>
          <p class="white--text subeheading mt-1 text-center">Username</p>
        </v-flex>
      </v-layout>

      <v-divider class="mb-4"></v-divider>

        <v-list>
          <v-list-item v-for="link in links" :key="link.text" router :to="link.route" active-class="border" link class="ma-2 tile">            
            <v-list-item-action>
                <v-icon>
                {{link.icon}}
                </v-icon>
            </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>{{link.text}}</v-list-item-title>
              </v-list-item-content>
          </v-list-item>
        </v-list>
      <template v-slot:append>
        <div class="pa-2">
          <v-btn block>
            Logout
          </v-btn>
        </div>
      </template>
      </v-navigation-drawer>
      <!-- MENU LATERAL -->


  </nav>
</template>


<script>
  export default {
    data: () => ({
        drawer:true,
        links: [
          { text: 'Dashboard', icon: 'mdi-view-dashboard' },
          { text: 'Account', icon: 'mdi-account-box' },
          { text: 'Admin', icon: 'mdi-gavel' },
        ],
   

  })
}
</script>

<style scoped>
  .tile {
    margin: 5px;
    border-radius: 4px;
  }
  .tile:hover {
    background: white;
  }
</style>