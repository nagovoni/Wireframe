<template>
  <v-app id="inspire">

    <v-app-bar>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>Chuck Norris Jokes</v-app-bar-title>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" temporary>


<v-divider></v-divider>

<v-list density="compact" nav>
            <v-list-item prepend-icon="mdi-home" title="Home" value="home"></v-list-item>
            <v-list-item prepend-icon="mdi-star" title="Favorites" value="favorites"></v-list-item>
 </v-list>
     </v-navigation-drawer>

    <v-main class="bg-grey-lighten-2">
      <v-container>
        <v-row>

        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
    data: () => ({
      drawer: false,
      routes: [
        { route: '/', name: 'Home'},
        { route: '/favorites', name: 'Favorites'},
      ]
     }),
  }
</script>



