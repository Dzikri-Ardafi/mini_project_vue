<template>
<div>
    <v-container>
        <ApolloQuery 
            :query="require('../../gql/MoviebyGenre/AdventureMovie.gql')"> 
                <template v-slot="{ result: { loading, error, data } }">
                                <!-- Loading -->
                    <div v-if="loading" class="loading apollo">Loading...</div>
                                <!-- Error -->
                    <div v-else-if="error" class="error apollo">An error occurred</div>
                                <!-- Result -->
                    <div v-else-if="data" class="result apollo">
                    
                      <div><br>
                      <v-row>
                          <v-col cols="6"><h1>Action</h1></v-col>
                      </v-row> 

                         <br>  
                        <v-row>
                            <v-col cols="3" justify-space-around mb-6  v-for="adventure in data.Genre_by_pk.Movies " :key="adventure.Title">
                                <v-card :loading="loading" style="border-radius: 10px" 
                                    class="mx-auto"
                                    max-width="200" 
                                    color="transparent"
                                    @click="goTo(adventure.Title)" 
                                >
                                    <v-img
                                        :src="adventure.Path_Poster"
                                        height="400px"
                                    ></v-img>
                                    <div class="text-left">
                                        <h4>{{adventure.Title}}</h4>
                                        <h5>{{adventure.Release}}</h5>
                                    </div> 
                                </v-card> <br>
                            </v-col>
                        </v-row>
                      </div>
                        
                    </div>
                </template>
  
  
    
                            
                        

        </ApolloQuery>
    </v-container>   
</div>
  
</template>

<script>
export default {
    name: 'AdventurePage',
    layout: 'moviePage',
    methods: {
    goTo(Title) {
      this.$router.push(`/detail/${Title}`);
    },
    }
}
</script>

<style>
  
</style>