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

            <v-form @submit="userLogin">
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
                <v-radio-group v-model="radioGroup" row>
                  <v-radio off-icon="mdi-information"  color="gray" label="Social Login" value="1" ></v-radio>
                  <v-radio off-icon="mdi-gmail" color="red" label="Login With Google" value="2" ></v-radio>
                  <v-radio off-icon="mdi-facebook" color="indigo"  label="Login With Facebook" value="3" ></v-radio>
                </v-radio-group>
                <v-card-text v-show="radioGroup==='1'">
                  <v-text-field
                    label="Username"
                    name="username"
                    prepend-inner-icon="mdi-account"
                    type="text"
                    v-model="login.username"
                    outlined
                  ></v-text-field>

                  <v-text-field
                    id="password"
                    label="Password"
                    name="password"
                    prepend-inner-icon="mdi-lock"
                    type="password"
                    v-model="login.password"
                    outlined
                  ></v-text-field>
                </v-card-text>
                <v-card-text v-show="radioGroup==='3'" class="col-md-12 align-content-center" >
                  <v-btn block class="align-center" color="primary" rounded  @click.prevent="loginWithFacebook()">Login With Facebook</v-btn>
                </v-card-text>
                <v-card-text v-show="radioGroup==='2'" >
                  <v-btn block  rounded color="error" @click.prevent="loginWithGoogleAccount()">Login With Google</v-btn>
                </v-card-text>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn color="primary" type="submit">Login</v-btn>
                </v-card-actions>
              </v-card>
            </v-form>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    middleware: ['auth'],
    layout: 'auth',
    data() {
      return {
        radioGroup: '2',
        login: {
          username: '',
          password: ''
        }
      }
    },
    methods: {
      async userLogin() {
        console.log("Try logging in ..." +  this.radioGroup)
        try {
          let response = await this.$auth.loginWith('social')
          console.log(response)
        } catch (err) {
          console.log(err)
        }
      },
      async loginWithFacebook(){
        try{
          await this.$auth.loginWith('facebook').catch(e => {
            console.log("Error log"+ e.toString())
          })

        }catch (e) {
          console.log(e)
        }
      },
      async loginWithGoogleAccount(){
        try{
           await this.$auth.loginWith('google').then(() => {
             console.log("Logged in!");
           }).catch(e => {
             console.log("Error log"+ e.toString())
           })


        }catch (e) {
          console.log(e)
        }
      }

    }
  }
</script>
