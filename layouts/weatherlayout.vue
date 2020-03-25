<template>
  <v-app>
    
    <v-content>
        
      <v-toolbar color="indigo" dark>

        <v-toolbar-side-icon></v-toolbar-side-icon>
        <v-toolbar-title>Weather App With Nuxt</v-toolbar-title>

        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">

          <v-btn text>

            <nuxt-link to="/"> Home </nuxt-link>

          </v-btn>
        

        </v-toolbar-items>

      </v-toolbar>

<transition>

</transition>

    <v-container>
        <nuxt />
      </v-container>

    </v-content>



  </v-app>
</template>

<script>
export default {
  
}
</script>


<style scoped>
a {
  text-decoration: none;
  color: white;
}
h1{
    color: white;
}

</style>




