<template>
  <v-app id="inspire">
    <v-main>
      <v-container
        class="fill-height"
        fluid
      >

        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="12"
            md="6"
          >

            <v-form>
              <v-card class="elevation-12">
                <v-toolbar
                  color="primary"
                  dark
                  flat
                >
                  <v-toolbar-title>Login form</v-toolbar-title>
                  <v-spacer></v-spacer>
                  <v-tooltip bottom>
                    <template v-slot:activator="{ on }">

                    </template>
                    <span>Source</span>
                  </v-tooltip>
                </v-toolbar>

                <v-card-text >
                  <h1>Logged In</h1>

                </v-card-text>

                <v-card-actions>
                </v-card-actions>
              </v-card>
            </v-form>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

