<template>
  <v-col class="col-sm-9" style="margin-left: 0px;margin-right:0px">
    <v-content cols="9" class="content" style="padding: 48px;">
      <!-- account overview view content -->
      <h1>Account overview</h1>
      <article class="section">
        <h3>Profile</h3>
        <section class="child">
          <table class="info-table">
            <colgroup>
              <col class="info-col" />
              <col class="info-col" />
            </colgroup>
            <tbody>
              <!-- The Username section -->
              <tr class="info-row">
                <td class="info-cell">
                  <label for="username"
                    ><span class="info-content">Username</span></label
                  >
                </td>
                <td class="info-cell">
                  <p class="info-value" id="username">{{ user.username }}</p>
                </td>
              </tr>
              <!-- The Email sction -->
              <tr class="info-row">
                <td class="info-cell">
                  <label for="email"
                    ><span class="info-content">Email</span></label
                  >
                </td>
                <td class="info-cell">
                  <p class="info-value">{{ user.userEmail }}</p>
                </td>
              </tr>
              <!-- The Gender sction -->
              <tr class="info-row">
                <td class="info-cell">
                  <label for="gender"
                    ><span class="info-content">Gender</span></label
                  >
                </td>
                <td class="info-cell">
                  <p class="info-value">{{ user.userGender }}</p>
                </td>
              </tr>
              <!-- The Date of birth scetion -->
              <tr class="info-row">
                <td class="info-cell">
                  <label for="date"
                    ><span class="info-content">Date of birth</span></label
                  >
                </td>
                <td class="info-cell">
                  <p class="info-value">{{ user.userDOB }}</p>
                </td>
              </tr>
              <!-- The User's country section -->
              <tr class="info-row">
                <td class="info-cell">
                  <label for="country"
                    ><span class="info-content">Country</span></label
                  >
                </td>
                <td class="info-cell">
                  <p class="info-value">{{ user.userCountry }}</p>
                </td>
              </tr>
            </tbody>
          </table>
        </section>
        <!-- Button to change the user's data -->
        <a class="btn-class" href="/account/edit">Edit profile</a>
      </article>
      <article class="section">
        <h3>Your plan</h3>
        <section class="child">
          <div class="card">
            <div class="card-header">
              <div class="card-title">
                <span
                  class="card-span-title"
                  v-if="this.$store.state.user.userType === 'normal'"
                  >Symphonia Free</span
                >
                <span
                  class="card-span-title"
                  v-if="this.$store.state.user.userType === 'premium'"
                  >Symphonia Premium</span
                >
              </div>
            </div>
            <div class="card-body">
              <div>
                <div class="card-body-plan">
                  <div class="card-body-plan-inside">
                    <p class="card-body-plan-content">
                      Play music in shuffle mode only, with ads.
                    </p>
                  </div>
                </div>
                <div>
                  <!-- The user's plan -->
                  <h3 v-if="this.$store.state.user.userType === 'noraml'">
                    Free
                  </h3>
                  <h3 v-if="this.$store.state.user.userType === 'premium'">
                    Premium
                  </h3>
                </div>
              </div>
            </div>
          </div>
        </section>
        <!-- If the user is free -->
        <a
          class="btn-class"
          href="/premium/?checkout=false"
          v-if="this.$store.state.user.userType == `normal`"
          >Join Premium</a
        >
      </article>
      <article class="section">
        <h3>Sign out everywhere</h3>
        <p class="card-body-plant-content">
          Sign out wherever you have Symphonia open, including the web, mobile,
          desktop or any other devices.
        </p>
        <div class="note">
          <div class="note-content">
            <span class="card-body-plant-content"
              >Note: This doesn’t include partner devices, such as Sonos and
              PlayStation. For more information about logging out (or unlinking)
              Symphonia from a partner device, check the device’s manufacturer
              guide.</span
            >
          </div>
        </div>
        <a class="btn-class" href="#">Sign out everywhere</a>
      </article>
      <bottom-content></bottom-content>
    </v-content>
  </v-col>
</template>

<script>
import BottomContent from "./BottomContent.vue";

/**
 * This page is used to overview the user data
 * @displayName User Overview
 * @example [none]
 */
export default {
  data() {
    return {
      /** The current user's data got from the created request */
      user: {}
    };
  },
  components: {
    /** The review section */
    "bottom-content": BottomContent
  },
  created() {
    /** Request to get the current user's data */
    this.$store
      .dispatch("userData")
      .then(() => {
        // If we got it set it into the data to display the user's info
        this.user = this.$store.state.user;
        this.user.userDOB = this.user.userDOB.slice(0, 10);
      })
      .catch();
  }
};
</script>

<style lang="sass" scoped>
@import "./style/overview.sass"
</style>
