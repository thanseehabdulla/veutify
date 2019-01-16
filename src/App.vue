<template>
  <v-app>
    <v-navigation-drawer
            v-model="drawerRight"
            fixed
            right
            clipped
            app
            temporary
    >
      <v-list>
        <v-list-tile>
          <v-list-tile-action>
            <v-icon>home</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Home</v-list-tile-title>
        </v-list-tile>

        <v-list-group
                prepend-icon="account_circle"
                value="true"
        >
          <v-list-tile slot="activator">
            <v-list-tile-title>Users</v-list-tile-title>
          </v-list-tile>

          <v-list-group
                  no-action
                  sub-group
                  value="true"
          >
            <v-list-tile slot="activator">
              <v-list-tile-title>Admin</v-list-tile-title>
            </v-list-tile>

            <v-list-tile
                    v-for="(admin, i) in admins"
                    :key="i"
                    @click=""
            >
              <v-list-tile-title v-text="admin[0]"></v-list-tile-title>
              <v-list-tile-action>
                <v-icon v-text="admin[1]"></v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list-group>

          <v-list-group
                  sub-group
                  no-action
          >
            <v-list-tile slot="activator">
              <v-list-tile-title>Actions</v-list-tile-title>
            </v-list-tile>

            <v-list-tile
                    v-for="(crud, i) in cruds"
                    :key="i"
                    @click=""
            >
              <v-list-tile-title v-text="crud[0]"></v-list-tile-title>
              <v-list-tile-action>
                <v-icon v-text="crud[1]"></v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list-group>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
            color="whiteblack"
            dark
            fixed
            app
            clipped-right
    >
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title>CENTRAL NRM DEBUGGING CONSOLE</v-toolbar-title>

      <v-spacer>
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link>|
      </v-spacer>
      <v-toolbar-side-icon @click.stop="drawerRight = !drawerRight"></v-toolbar-side-icon>
    </v-toolbar>
    <v-navigation-drawer
            v-model="drawer"
            fixed
            app
    >
      <v-list>
        <v-list-tile>
          <v-list-tile-action>
            <v-icon>home</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Home</v-list-tile-title>
        </v-list-tile>

        <v-list-group
                prepend-icon="account_circle"
                value="true"
        >
          <v-list-tile slot="activator">
            <v-list-tile-title>Users</v-list-tile-title>
          </v-list-tile>

          <v-list-group
                  no-action
                  sub-group
                  value="true"
          >
            <v-list-tile slot="activator">
              <v-list-tile-title>Admin</v-list-tile-title>
            </v-list-tile>

            <v-list-tile
                    v-for="(admin, i) in admins"
                    :key="i"
                    @click=""
            >
              <v-list-tile-title v-text="admin[0]"></v-list-tile-title>
              <v-list-tile-action>
                <v-icon v-text="admin[1]"></v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list-group>

          <v-list-group
                  sub-group
                  no-action
          >
            <v-list-tile slot="activator">
              <v-list-tile-title>Actions</v-list-tile-title>
            </v-list-tile>

            <v-list-tile
                    v-for="(crud, i) in cruds"
                    :key="i"
                    @click=""
            >
              <v-list-tile-title v-text="crud[0]"></v-list-tile-title>
              <v-list-tile-action>
                <v-icon v-text="crud[1]"></v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list-group>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>
    <v-navigation-drawer
            v-model="left"
            temporary
            fixed
    ></v-navigation-drawer>
    <v-content>

      <router-view/>
    </v-content>
    <v-navigation-drawer
            v-model="right"
            right
            temporary
            fixed
    ></v-navigation-drawer>
    <v-footer color="whiteblack" class="white--text" app>
      <span>@Global Eagle Entertainment</span>
      <v-spacer></v-spacer>
      <!--<span>&copy; 2017</span>-->
    </v-footer>

  </v-app>
</template>

<script>

export default {
  name: 'App',
  data: () => ({
    drawer: null,
    drawerRight: null,
    right: false,
    left: false,
    admins: [
      ['Management', 'people_outline'],
      ['Settings', 'settings']
    ],
    cruds: [
      ['Create', 'add'],
      ['Read', 'insert_drive_file'],
      ['Update', 'update'],
      ['Delete', 'delete']
    ]
  }),
  props: {
    source: String
  }
}


</script>
<style scoped>
  .whiteblack {
    background-color: #fff !important;
    border-color: #fff !important;
    color:black !important;
  }
  .v-btn .v-btn__content .v-icon {
    color: black;
  }
</style>