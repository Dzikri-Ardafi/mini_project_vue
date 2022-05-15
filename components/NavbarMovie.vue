<template>
  <div>
    <v-app-bar
      color="cyan darken-4"
      elevation="0"
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-btn color="transparent" elevation="0" to="/home"><h2>Home</h2></v-btn>

      <div class="text-center">
        <v-menu
          open-on-hover
          bottom
          offset-y>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
            
            color="transparent"
            elevation="0"
            v-bind="attrs"
            v-on="on"><h3>Genre</h3></v-btn> 
          </template>
      <v-list color="blue-grey darken-4" dense height="130" width="250">
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
  <v-btn
            style="margin-top: 1px"
            color="transparent" 
            elevation="0"
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

      <v-menu
        left
        bottom
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            icon
            v-bind="attrs"
            v-on="on"
          >
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item
            v-for="n in 5"
            :key="n"
            @click="() => {}"
          >
            <v-list-item-title>Option {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
  </div>
</template>