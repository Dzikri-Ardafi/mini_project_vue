<template>
<div>
    <v-app class="dark">
      
  <v-container fluid class="jangancontainer" style="height: 420px">
    
    <v-row>
      <v-col cols="12">
        <NavbarHome />
      </v-col>
    </v-row>
    <!-- Left Row -->
    <v-row>
      <v-col cols="6">
        <div style="margin-top: 75px">
          <h1 class="text-center font-weight-bold">Happy <span class="font-weight-regular">Watching "nama user"</span> </h1>
            <v-btn
            color="#BF360C"
            elevation="2"
            small
            style="margin-left:120px">Lets Watch</v-btn>
        </div>
      </v-col>

      <!-- Right Row -->
  
      <v-col cols="6">
  <ApolloQuery 
    :query="require('../gql/queries/HomeImage.gql')"> 
  <template v-slot="{ result: { loading, error, data } }">
  <!-- Loading -->
        <div v-if="loading" class="loading apollo">Loading...</div>
  <!-- Error -->
        <div v-else-if="error" class="error apollo">An error occurred</div>
  <!-- Result -->
      <div v-else-if="data" class="result apollo">
        <v-carousel 
        height="290"
        cycle
        hide-delimiter-background
        >
    <v-carousel-item
      v-for="newItem in data.Home_by_pk.Movies"
      :key="newItem.Title" 
      
      class="mx-auto"
      
      reverse-transition="fade-transition"
      transition="fade-transition"
      style="border-radius: 20px"
    >
    <v-img style="border-radius: 10px; margin-bottom: auto"
      :src="newItem.Path_image"
      class="mx-auto"
      max-height="290px"
      max-width="500px"
    ></v-img>
    </v-carousel-item>
  </v-carousel>
      </div>
  </template>

  </ApolloQuery>
    <template v-slot:prev="{ on, attrs }">
      <v-icon
        v-bind="attrs"
        v-on="on"
        color="white"
        size="48"
        v-text="'mdi-chevron-left'"
      ></v-icon>
    </template>
    <template v-slot:next="{ on, attrs }">
      <v-icon
        v-bind="attrs"
        v-on="on"
        color="white"
        size="48"
        v-text="'mdi-chevron-right'"
      ></v-icon>
    </template>
    <v-window-item
      v-for="n in 5"
      :key="`card-${n}`"
    >
      <v-img style="border-radius: 10px; margin-bottom: auto"
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      class="mx-auto"
      max-height="290px"
      max-width="500px"
    ></v-img>
    </v-window-item>
    
      </v-col>
    
    </v-row>
  </v-container>     
    

  <Nuxt />
    </v-app>
</div>
</template>

<script>


export default {
    name: 'HomeLayout',
    data: () => ({
      model: null,
      }),
}
</script>

<style>
    .jangancontainer{
      background-image: url("../static/h.jpg"); 
      
    };
    #container1{
      background-color: rgb(0, 1, 51);
      
    }
    

</style>