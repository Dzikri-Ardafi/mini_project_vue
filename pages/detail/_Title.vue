<template>
<v-container>
    
    <ApolloQuery
      :query="require('../../gql/getMovieby/getMoviebyTitle.gql')"
      :variables="{ Title: Title }"
    >
      <template v-slot="{ result: { loading, error, data } }">
        <!-- Loading -->
        <div v-if="loading" class="loading apollo">Loading...</div>

        <!-- Error -->
        <div v-else-if="error" class="error apollo">An error occurred</div>

        <!-- Result -->
        <div v-else-if="data" class="result apollo">
            <v-row>
                <v-col cols="6">
                    <v-card
                        :loading="loading"
                        class="my-5 mx-auto"
                        max-width="374"
                        color="transparent"
                        elevation="0">
                        <v-img
                            style="border-radius: 10px"
                            height="500"
                            max-width="400"
                            :src="data.Movies_by_pk.Path_Poster">
                        </v-img>
                        <v-card-text>
                            <v-row
                                align="center"
                                class="mx-12">
                            
                                <v-rating
                                    :value="data.Movies_by_pk.Rating/2"
                                    color="amber"
                                    dense
                                    half-increments
                                    readonly
                                    size="18"
                                    class="mx-5"
                                ></v-rating> 
                                <h4 style="margin-top:3px">{{data.Movies_by_pk.Rating}} ({{data.Movies_by_pk.View}}) </h4>
                            </v-row>
                        </v-card-text>
                        <v-btn block class="red accent-4" style="border-radius: 15px">
                            Watch Trailer 
                            <span class="mx-1">
                                <v-icon>
                                    mdi-youtube
                                </v-icon>
                            </span>
                        </v-btn>
                    </v-card>
                </v-col>

                <v-col cols="6">
                    <v-card color="dark" height="570" class="my-5 mx-auto">
                    <br>
                    <v-row>
                        <v-col cols="12" class="d-flex">
                            <v-row class="d-flex">
                               <v-col cols="9" >
                            <h2 class="mx-4">{{data.Movies_by_pk.Title}}</h2> </v-col>  
                            <v-col class="mx-4"> 
                                <div class="d-flex">
                            <v-tooltip bottom>
                                <template v-slot:activator="{ on, attrs }">
                                    <v-btn 
                                        color="red"
                                        icon 
                                        v-bind="attrs"
                                        v-on="on">
                                            <v-icon>
                                                mdi-heart
                                            </v-icon>
                                    </v-btn>
                                </template>
                                    <span>Add to Your Favorite Movie</span>
                            </v-tooltip>
                            <v-tooltip bottom>
                                <template v-slot:activator="{ on, attrs }">
                                    <v-btn 
                                        icon 
                                        v-bind="attrs"
                                        v-on="on">
                                            <v-icon>
                                                mdi-clock
                                            </v-icon>
                                    </v-btn>
                                </template>
                                    <span>Watch Later</span>
                            </v-tooltip>
                                </div>
                            </v-col>
                            </v-row>
                        </v-col>
                    </v-row> <br> <hr>
                    <v-simple-table> 
                        <template v-slot:default>                  
                            <tbody> 
                                <tr>
                                    <td><h2>Genre:</h2></td>
                                    <td><h3>{{data.Movies_by_pk.Genre}}</h3></td>
                                </tr>
                                <tr>
                                    <td><h2>Duration:</h2></td>
                                    <td><h3>{{data.Movies_by_pk.Duration}}</h3></td>
                                </tr>
                                <tr>
                                    <td><h2>Release:</h2></td>
                                    <td><h3>{{data.Movies_by_pk.Release}}</h3></td>
                                </tr>
                                <tr>
                                    <td><h2>Synopsis:</h2></td>
                                    <td><h3>{{data.Movies_by_pk.Synopsis}}</h3></td>
                                </tr><tbody></tbody>
                            </tbody>
                        </template>
                    </v-simple-table>
                    </v-card>
                </v-col>
            </v-row>

        </div>

        <!-- No result -->
        <div v-else class="no-result apollo">No result :(</div>
      </template>
    </ApolloQuery>
  
</v-container>
  
</template>

<script>
export default {
    name: 'DetailPage',
    layout: 'moviePage',
    data () {
      return {
        desserts: [
          {
            name: 'Genre',
            
          },
          {
            name: 'Duration',
            
          },
          {
            name: 'Release',
            
          },
          {
            name: 'Synopsis',
            
          },
        ],
      }
    },
    computed: {
    Title() {
      return this.$route.params.Title;
    },
  },
    
}
</script>

<style>

</style>