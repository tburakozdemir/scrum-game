<template>
  <div class="user">
    <div
      class="card-user"
      v-bind:style="hasUserSelectedNum && 'background-color: #3993ff;'"
    >
      <h6 v-if="isSelectedNumHidden == true">
        {{ this.clikedItems[0].number }}
      </h6>
      <div class="card-user-name">
        <h6>{{ this.userName }}</h6>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    "userName",
    "hasUserSelectedNum",
    "isSelectedNumHidden",
    "clikedItems",
  ],
};
</script>

<style>
.card-user {
  width: 40px;
  height: 70px;
  background: #e8e9ea;
  border-radius: 10px;
  cursor: pointer;
}

.card-user:active {
  background-color: #3993ff;
}

.card-user {
  text-align: center;
  padding: 25px 0;
}

.card-user-name h6 {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-size: 1rem;
  font-weight: 700;
  line-height: 1.2em;
  padding-top: 3.5rem;
  width: 3rem;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: inherit;
}
</style>