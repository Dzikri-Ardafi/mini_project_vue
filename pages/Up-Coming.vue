<template>
<div>
    <v-container>
        <ApolloQuery 
            :query="require('../gql/condition/upComing.gql')"> 
                <template v-slot="{ result: { loading, error, data } }">
                                <!-- Loading -->
                    <div v-if="loading" class="loading apollo">Loading...</div>
                                <!-- Error -->
                    <div v-else-if="error" class="error apollo">An error occurred</div>
                                <!-- Result -->
                    <div v-else-if="data" class="result apollo">
                    
                      <div><br>
                      <v-row>
                          <v-col cols="6"><h1>Up Coming</h1></v-col>
                      </v-row> 

                         <br>  
                        <v-row>
                            <v-col cols="3" justify-space-around mb-6  v-for="up in data.Condition_by_pk.Movies " :key="up.Title">
                                <v-card :loading="loading" style="border-radius: 10px" 
                                    class="mx-auto"
                                    max-width="200" 
                                    color="transparent" 
                                    @click="goTo(up.Title)"
                                >
                                    <v-img
                                        :src="up.Path_Poster"
                                        height="400px"
                                    >
                                    <v-avatar size="45" tile color="indigo darken-4">
                    {{up.Rating}} <span><v-icon small color="orange">mdi-star</v-icon></span> 
                  </v-avatar></v-img>
                                    <div class="text-left">
                                        <h4>{{up.Title}}</h4>
                                        <h5>{{up.Release}}</h5>
                                    </div> 
                                </v-card> <br>
                            </v-col>
                        </v-row>
                      </div>
                        
                    </div>
                    <div v-else class="no-result apollo text-center" >
            <h4>Getting Your Movies</h4>
            <v-icon large>mdi-spin mdi-loading</v-icon> 
        </div>
                </template>
  
  
    
                            
                        

        </ApolloQuery>
    </v-container>   
</div>
  
</template>

<script>
export default {
    name: 'UpcomingPage',
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