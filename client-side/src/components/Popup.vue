<template>
  <div>
    <b-modal ref="my-modal" hide-footer title="Please Enter User Name">
      <div class="d-block">
        <form ref="form" @submit.stop.prevent="handleSubmit">
          <b-form-group
            label="User Name"
            label-for="name-input"
            invalid-feedback="Name is required"
          >
            <b-form-input
              id="name-input"
              v-model="name"
              required
            ></b-form-input>
          </b-form-group>
          <br />
          <b-button variant="outline-primary" type="submit">Submit</b-button>
        </form>
      </div>
    </b-modal>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
    };
  },
  methods: {
    showModal() {
      this.$refs["my-modal"].show();
    },
    hideModal() {
      this.$refs["my-modal"].hide();
    },
    handleSubmit(event) {
      event.preventDefault();
      this.$emit("getUsername", this.name);
      this.hideModal();
    },
  },
  mounted() {
    this.showModal();
  },
};
</script>