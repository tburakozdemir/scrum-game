<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-md-6 offset-md-3">
          <Signup />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Signup from "../components/Signup.vue";

export default {
  name: "app",
  components: {
    Signup,
  },
};
</script>

<style>
