<template>
<div class="apps" >  

<!-- Get Top Rating Movies -->
<v-container >
<ApolloQuery 
:query="require('../gql/queries/TopRating.gql')"> 
<template v-slot="{ result: { loading, error, data } }">
  <!-- Loading -->
        <div v-if="loading" class="loading apollo">Loading...</div>
  <!-- Error -->
        <div v-else-if="error" class="error apollo">An error occurred</div>
  <!-- Result -->
      <div v-else-if="data" class="result apollo">
  <h2>Top Movie</h2>
  
        <v-row >
          <v-col cols="1"></v-col>
          <v-col cols="10" class="d-flex justify-space-around mb-6">
            
            <v-card style="border-radius: 10px" v-for="movie in data.Condition_by_pk.Movies "
                  :key="movie.Title"
                  max-width="200"  
                  color="transparent">
                <v-img
                  :src="movie.Path_Poster"
                  height="400px"
                  max-width="auto">
                </v-img>
                <h4>
                  {{movie.Title}}
                </h4>
 <v-card-text>
  {{movie.Release}}
</v-card-text>
            </v-card>
           
          </v-col>
          <v-col cols="1" class="my-auto">
            <h3>View All</h3>
            <v-btn
              class="mx-2"
              fab
              small
              color="orange darken-4"
            > 
              <v-icon color="black" size="40">
                mdi-arrow-right
              </v-icon>
            </v-btn>
           </v-col>
        </v-row>
  </div>
 </template>
   <br>
</ApolloQuery>
</v-container>

<!-- Get Indonesia Movies Movies -->
  <v-container >
        
    <ApolloQuery 
:query="require('../gql/queries/IndonesiaMovies.gql')"

> 
<template v-slot="{ result: { loading, error, data } }">
  <!-- Loading -->
        <div v-if="loading" class="loading apollo">Loading...</div>
  <!-- Error -->
        <div v-else-if="error" class="error apollo">An error occurred</div>
  <!-- Result -->
        <div v-else-if="data" class="result apollo">
  <h2>Indonesia Movies</h2>
  
    <v-row >
    <v-col cols="1"></v-col>
    <v-col cols="10" class="d-flex justify-space-around mb-6">
      <v-card style="border-radius: 10px" v-for="Indonesia in data.Condition_by_pk.Movies "
      :key="Indonesia.Title"
       max-width="200"
       color="transparent"  
  >
    <v-img
      :src="Indonesia.Path_Poster"
      height="400px"
    ></v-img>

    <h4>
      {{Indonesia.Title}}
    </h4>

    
  </v-card>
  
    </v-col>
    <v-col cols="1" class="my-auto">
      <h3>View All</h3>
      <v-btn
      class="mx-2"
      fab
      small
      color="orange darken-4"
    >
      <v-icon color="black" size="40">
        mdi-arrow-right
      </v-icon>
    </v-btn>
    </v-col>
    </v-row>
  </div>
  </template>
   <br>
</ApolloQuery>
  </v-container>
  

<!-- Get For Kids Movies -->
 <v-container >
        
    <ApolloQuery 
:query="require('../gql/queries/ForKids.gql')"

> 
<template v-slot="{ result: { loading, error, data } }">
  <!-- Loading -->
        <div v-if="loading" class="loading apollo">Loading...</div>
  <!-- Error -->
        <div v-else-if="error" class="error apollo">An error occurred</div>
  <!-- Result -->
        <div v-else-if="data" class="result apollo">
  <h2>For Kids</h2>
  
    <v-row >
    <v-col cols="1"></v-col>
    <v-col cols="10" class="d-flex justify-space-around mb-6">
      <v-card style="border-radius: 10px" v-for="kids in data.Condition_by_pk.Movies "
      :key="kids.Title"
       max-width="200" 
       color="transparent" 
  >
    <v-img
      :src="kids.Path_Poster"
      height="400px"
    ></v-img>
<div class="text-left">
    <h4>
      {{kids.Title}}
    </h4>
<h5>{{kids.Release}}</h5>
</div>   
      
    
  </v-card>
  
    </v-col>
    <v-col cols="1" class="my-auto">
      <h3>View All</h3>
      <v-btn
      class="mx-2"
      fab
      small
      color="orange darken-4"
    >
      <v-icon color="black" size="40">
        mdi-arrow-right
      </v-icon>
    </v-btn>
    </v-col>
    </v-row>
  </div>
  </template>
   <br>
</ApolloQuery>
  </v-container>
    
</div>
        
</template>

<script>
export default {
    name: "HomePage",
    layout: 'homePage',


    
}
   
</script>

<style>
  .apps{
    background-color: rgb(0, 0, 24);
  }
</style>