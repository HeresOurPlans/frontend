<template>
    <b-navbar toggleable="lg" type="dark" variant="dark">
      
    <b-navbar-brand>Here's Our Plan</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="/main">Home</b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-item href="/profilePage">{{ getCurrentUserName() }}</b-nav-item>

        <b-nav-form>
          <b-col>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search Locations"></b-form-input>
          </b-col>
          <b-col>
          <b-button size="sm" class="my-2 my-sm-0" type="submit" href="/new_loc_map">Search</b-button>
          </b-col>
        </b-nav-form>

        <b-nav-item-dropdown text="Where to?" class="ml-2">
          <b-dropdown-item href="/itinerary">Itinerary</b-dropdown-item>
          <b-dropdown-item href="/additinerary">Add Activity</b-dropdown-item>
          <b-dropdown-item href="/map">Map</b-dropdown-item>
        </b-nav-item-dropdown>

        <b-nav-item href="#" class = "profileCircle">
          <b-nav-item-dropdown class="m-md-2" no-caret>
            <b-dropdown-item href="/profileEdit">Edit Profile</b-dropdown-item>
            <b-dropdown-item href="/logout">Log Out</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-nav-item>

      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
import jwt_decode from "jwt-decode"

export default {
    name: 'Navbar',
    fetchOnServer: false,
    methods: {
      getCurrentUserName() {
        if (process.browser) {
          const token = localStorage.getItem("token")
          if (token === null) {
            return "Guest"
          } else {
            const decoded_token = jwt_decode(token)
            console.log(decoded_token)
            return decoded_token["user"]
          }
        }
      },
      doSomething(){
        console.log('shown');
      }
    }
}
</script>

<style scoped>
.navbar.navbar-dark.bg-dark{
    background-color: #b6ad90!important;
}

.profileCircle{
        position: relative;
        width: 40px;
        height: 40px;
        -webkit-border-radius: 20px;
        -moz-border-radius: 20px;
        border-radius: 20px;
        background: black;
        transform: translateX(5%) translateY(-10%);
}
</style>