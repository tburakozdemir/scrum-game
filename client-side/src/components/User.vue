<template>
  <div class="user">
    <div style="display: flex; flex-direction: column; align-items: center">
      <div
        class="card-user"
        v-bind:style="hasUserSelectedNum && 'background-color: #3993ff;'"
      >
        <p v-if="isSelectedNumHidden == true">
          {{ showNumber }}
        </p>
      </div>
      <div class="card-user-name">
        <p>{{ this.userName }}</p>
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
    "showNumber",
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
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-size: 1rem;
  font-weight: 700;
  line-height: 2em;
  padding-top: 2.5rem;
  width: 3rem;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: inherit;
}
</style>