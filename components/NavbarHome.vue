<template>
  <div>
    <v-app-bar
      color="transparent"
      elevation="0"
    >
      
<div class="mx-5">
      <div class="text-center">
        <v-menu
          open-on-hover
          bottom
          offset-y>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
            color="transparent" 
            v-bind="attrs"
            v-on="on"><h3>Genre</h3></v-btn> 
          </template>
      <v-list color="transparent" dense height="135" width="250">
        <v-row>
          <v-col cols="6">
            <v-btn to="/genre/action" color="transparent" elevation="0"> Action </v-btn>
            <v-btn to="/genre/adventure" color="transparent" elevation="0"> Adventure </v-btn>
            <v-btn to="/genre/cartoon" color="transparent" elevation="0"> Cartoon </v-btn>
          </v-col>
          <v-col cols="6">
            <v-btn to="/genre/comedy" color="transparent" elevation="0"> Comedy </v-btn>
            <v-btn to="/genre/crime" color="transparent" elevation="0"> Crime </v-btn>
            <v-btn to="/genre/horror" color="transparent" elevation="0"> Horror </v-btn>
          </v-col>
        </v-row>
      </v-list>
    </v-menu>
  </div>
</div>
      <v-btn to="/Up-Coming"
            color="transparent" 
            v-bind="attrs"
            v-on="on">
              <h3>Up Coming</h3>
      </v-btn>
      <v-spacer></v-spacer>
      


      <v-col
          cols="12"
          sm="8"
          md="5"
        >
          <v-text-field
          style="margin-top: 25px"
            label="Search Your Favorite Movie Here"
            outlined
            dense
          ></v-text-field>
        </v-col>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      
    </v-app-bar>
  </div>
</template>

