<template>
  <div>
    <b-modal
      ref="my-modal"
      id="modal-no-backdrop"
      hide-backdrop
      content-class="shadow"
      title="⚠️ Error Message ⚠️"
    >
      <p class="my-2">Please select a <code>'number'</code> down below!</p>
    </b-modal>
  </div>
</template>

<script>
export default {
  methods: {
    showModal() {
      this.$refs["my-modal"].show();
    },
    hideModal() {
      this.$refs["my-modal"].hide();
    },
    handleSubmit(event) {
      event.preventDefault();
      this.hideModal();
    },
  },
  mounted() {
    this.showModal();
  },
};
</script>