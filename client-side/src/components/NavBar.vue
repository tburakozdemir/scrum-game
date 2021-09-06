<template>
  <div>
    <b-navbar type="light" variant="light">
      <b-navbar-toggle target="nav-text-collapse"></b-navbar-toggle>

      <b-navbar-brand href="#">
        <b-avatar
          src="https://img.icons8.com/ios-filled/100/100/crow.png"
        ></b-avatar>
      </b-navbar-brand>

      <b-collapse id="nav-text-collapse" is-nav>
        <b-navbar-nav class="right-nav">
          <b-nav-text>
            <h5>
              <b>Game Name: {{ gameName }}</b>
            </h5>
          </b-nav-text>
          <div style="display: flex">
            <b-button variant="outline-primary">📮 Invite Players</b-button>
            <b-nav-item-dropdown left>
              <template #button-content>
                <em>{{ userName }}</em>
              </template>
              <b-dropdown-item href="#">Profile</b-dropdown-item>
              <b-dropdown-item href="/about">About</b-dropdown-item>
              <b-dropdown-item href="/">Sign Out</b-dropdown-item>
            </b-nav-item-dropdown>
          </div>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
  props: ["userName", "gameName"],

  created: function () {
    console.log(this.userName);
  },
};
</script>

<style>
.right-nav {
  width: 100%;
  justify-content: space-between;
  align-items: center;
}
</style>