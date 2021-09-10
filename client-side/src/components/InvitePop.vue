<template>
  <div>
    <b-modal
      ref="my-inv-link"
      id="modal-no-backdrop"
      hide-backdrop
      content-class="shadow"
      title="Invite Players"
    >
      <p class="my-2">Invite Link</p>
    </b-modal>
  </div>
</template>

<script>
export default {
  methods: {
    showModal() {
      this.$refs["my-inv-link"].show();
    },
    hideModal() {
      this.$refs["my-inv-link"].hide();
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