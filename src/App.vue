<template>
 <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
      src="https://wallpapercave.com/wp/wp2552650.jpg"
    >
    <v-row class="pa-8 justify-center">
      <v-col class="justify-center">
        <v-btn  
        v-for="link in linkovi" 
        :key="link" 
        :to="link.path" 
        color="primary"
        class="justify-center"><v-spacer></v-spacer>{{ link.text }}</v-btn>
      </v-col></v-row>
      <v-row class="justify-center">
    <v-col cols="8">
    <v-card
      flat
    >
      <v-toolbar
        flat
        rounded
        height="50"
      >
        <v-switch
          style="padding-top: 20px"
          v-model="$vuetify.theme.dark"
          inset
          label="Svjetlina"
          persistent-hint
          color="error"
        ></v-switch>
      </v-toolbar>

      
      </v-card>
      </v-col>
    </v-row>
    </v-navigation-drawer>

    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title><a href="/"><img class="logo" src="https://myplaceloungechiangmai.com/wp-content/uploads/2017/07/NBA-logo-png-download-free.png" width="100px" style="padding-top:5px"></a></v-toolbar-title>
    </v-app-bar>
    

    <v-main>
      <router-view/>
    </v-main>






    <v-card
      class="flex-auto justify-center"
      flat
      rounded
      src="https://myplaceloungechiangmai.com/wp-content/uploads/2017/07/NBA-logo-png-download-free.png"
    >
      <v-card-title class="blue darken-1 justify-center">
        <v-btn
          v-for="ikona in ikone"
          :key="ikona"
          v-bind:href="ikona.path"
          class="mx-4"
          dark
          icon
        >
          <v-icon size="24px">
            {{ ikona.slika }}
          </v-icon>
        </v-btn>
      </v-card-title>
    </v-card>

  </v-app>

</template>


<script>

export default {
  name: 'App',

  data: () => ({
    linkovi: [{text:"O meni", path:"/about"}, {text:"Doniraj", path:"/donate"}],
    ikone: [{slika:'mdi-facebook', path:"http://www.facebook.com/profile.php?id=100007123185072"},{slika:'mdi-youtube', path:"https://www.youtube.com/user/emza2k12"},{slika:'mdi-instagram', path:"https://www.instagram.com/emerik.juric97/"}],
    drawer: false
  }),
};
</script>


<style scoped>
  .logo {
    transition: transform 1s;
  }
  .logo:hover{
    transform:scale(1.04);
  }
  .v-navigation-drawer {
    transition: 1s;
  }
  .v-navigation-drawer:hover {
    zoom: 70px;
  }

</style>