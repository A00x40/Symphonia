<template>
  <!-- App.vue -->
  <v-app>
    <!-- Sizes your content based upon application components -->
    <navBar />
    <v-content>
      <notification-popup></notification-popup>
      <!-- Provides the application the proper gutter -->
      <premiumAds></premiumAds>
      <v-container fluid>
        <div class="container">
          <!-- the main container to the side bad & view router -->
          <div class="row" style="width: 1185px; margin:0px;">
            <!-- Side bar content -->
            <side-bar></side-bar>
            <!-- Views go here from side bar -->
            <router-view></router-view>
          </div>
        </div>
      </v-container>
    </v-content>
    <appFooter />
  </v-app>
</template>

<script>
import PreAds from "../components/User Settings/PremiumAds.vue";
import SideBar from "../components/User Settings/SideBar.vue";
import navBar from "../components/Homepage/TheHomepageNavigationBar.vue";
import appFooter from "../components/Homepage/TheHomepageFooter.vue";
import NotificationPopup from "../components/Notifications/NotificationPopUp";
import isLoggedIn from "../mixins/userService/isLoggedIn";
import isNotificationsAllowed from "../mixins/userService/isNotificationsAllowed";
import getuserToken from "../mixins/userService/getUserToken";

export default {
  /**
   * This page is used to show user settings
   * @displayName User Settings
   * @example [none]
   */

  components: {
    // Components to render
    premiumAds: PreAds,
    "side-bar": SideBar,
    navBar: navBar,
    appFooter: appFooter,
    NotificationPopup
  },
  created() {
    // check if the user logged in
    if (this.isLoggedIn()) {
      if (this.isNotificationsAllowed()) {
        //get registration token from the user if the user is logged in
        this.$store.dispatch(
          "notification/getRegistrationToken",
          this.getuserToken()
        );
        //set up a listener to catch notification messages in webhome
        this.$store.dispatch("notification/setRecieveNotificationHandler");
        //set up a listener for any change in token in the fcm server to refersh the token
        this.$store.dispatch("notification/setRefreshTokenHandler");
      }
    }
  },
  mixins: [isLoggedIn, isNotificationsAllowed, getuserToken]
};
</script>

<style scoped>
@font-face {
  font-family: Circular;
  src: url("https://open.scdn.co/fonts/CircularSpUIv3T-Book.woff2")
      format("woff2"),
    url("https://open.scdn.co/fonts/CircularSpUIv3T-Book.woff") format("woff"),
    url("https://open.scdn.co/fonts/CircularSpUIv3T-Book.ttf") format("ttf");
  font-style: normal;
  font-weight: 400;
}
.v-content {
  display: block;
  opacity: 1;
  transition: opacity 0.2s ease-in-out;
  display: -moz-flex;
  display: -ms-flexbox;
  display: -ms-flex;
  display: -webkit-box;
  display: flex;
  -moz-flex-direction: column;
  -ms-flex-direction: column;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  flex-direction: column;
  -moz-flex: 1;
  -ms-flex: 1;
  -webkit-box-flex: 1;
  flex: 1;
  background-image: linear-gradient(#212c39, #121e3d 50%, #000);
  background-repeat: no-repeat;
}
.container {
  padding: 0;
}
.row {
  width: 1185px;
  margin: 0;
}
</style>
