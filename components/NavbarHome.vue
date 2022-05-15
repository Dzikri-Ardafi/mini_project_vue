<template>
  <div>
    <v-app-bar
      color="transparent"
      elevation="0"
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title class="mx-5">Genre</v-toolbar-title> 
      <v-toolbar-title>Up Coming</v-toolbar-title>
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
          >suatu</v-text-field>
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