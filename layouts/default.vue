<template>
  <v-app>
    <v-content >
      <!-- desktop -->
      <!-- <div class="d-none d-md-block"></div> -->
      <!-- mobile -->
      <div class="d-block">
        <v-container fluid class="accent">
          <v-row no-gutters align="center" justify="start">
            <v-col cols="1" class="flex-grow-0 flex-shrink-0">
              <v-icon @click="drawer = true">mdi-menu</v-icon>
            </v-col>
            <v-col
              cols="1"
              style="min-width: 100px; max-width:100%;"
              class="flex-grow-1 flex-shrink-0"
            >
              <v-row no-gutters align="center" justify="center">
                <nuxt-link to="/">
                  <v-row no-gutters align="center" justify="center">
                    <h3 class="logo">Clauddy</h3>
                  </v-row>
                </nuxt-link>
              </v-row>
            </v-col>
          </v-row>
        </v-container>
        <v-navigation-drawer v-model="drawer" fixed left class="d-block">
          <v-container fluid class="jello-topbar">
            <v-row no-gutters align="center" justify="space-between">
              <v-icon @click="drawer = false">mdi-close</v-icon>

              <v-row no-gutters align="center" justify="end">
                <p class="jello-user">Signed in as<br>
                  {{ $nuxt.$fire.auth.currentUser.email }}</p>
                &nbsp;
                <v-icon>mdi-account-circle-outline</v-icon>
              </v-row>

            </v-row>
          </v-container>
          <v-container class="d-block menu-items">
            <div class="d-flex flex-column">
              <div class="d-flex">
                <br />

              </div>
              <div class="d-flex">
                <nuxt-link to="/">
                  <v-icon>mdi-view-dashboard-variant-outline</v-icon>&nbsp;&nbsp;<b>My Boards</b>
                </nuxt-link>
              </div>
              <div class="d-flex">
                <nuxt-link to="/auth/signout">
                  <v-icon>mdi-exit-to-app</v-icon>&nbsp;&nbsp;<b>Sign out</b>
                </nuxt-link>
              </div>
              <div class="d-flex">
                <a @click="dialogSettings = true">
                  <v-icon>mdi-cog-outline</v-icon>&nbsp;&nbsp;<b>Settings</b>
                </a>
                <v-dialog v-model="dialogSettings" persistent max-width="600px">
                  <v-card elevation="0">
                    <v-card-title>
                      <span class="headline">Settings</span>
                    </v-card-title>
                    <v-toolbar
                      flat
                      height="72"
                    >
                      <v-switch
                        v-model="$vuetify.theme.dark"
                        inset
                        label="Dark Theme"
                        persistent-hint
                      ></v-switch>
                    </v-toolbar>

                    <v-card-actions>
                      <v-spacer></v-spacer>
                      <v-btn color="blue darken-1" text @click="dialogSettings = false">
                        Close
                      </v-btn>
                    </v-card-actions>
                  </v-card>
                </v-dialog>

              </div>
            </div>
          </v-container>
        </v-navigation-drawer>
      </div>
      <!-- content -->
      <nuxt />
    </v-content>
  </v-app>
</template>

<script>
  export default {
    data() {
      return {
        drawer: false,
        dialogSettings: false,
      }
    },
  }
</script>

<style lang="scss" scoped>
  .v-card-container {
    padding: 0 20px;
  }

  .v-application a {
    text-decoration: none;
  }

  .menu-items a {
    padding: 10px 0px 10px 3px;
    font-size: 24px;
  }

  .card-subtitle {
    display: block;
    margin: 10px 0 2px;
    font-size: 16px;
    color: #000000;
  }
</style>
