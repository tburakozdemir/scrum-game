<template>
  <div class="game">
    <NavBar 
      :userName="userName" 
      :gameName="gameName" 
    />
    <Popup 
      @getUsername="getUserName($event)" 
    />
    <Error 
      v-if="error == true" 
    />
    <div class="container-table">
      <div class="game-table">
        <b-button
          v-on:click="getAverage"
          class="table-but"
          pill
          variant="primary"
          >Show Cards</b-button
        >
      </div>
    </div>
    <br />
    <User
      :userName="userName"
      :hasUserSelectedNum="hasUserSelectedNum"
      :isSelectedNumHidden="isSelectedNumHidden"
      :clikedItems="clikedItems"
    />
    <div class="average-card">
      <b-card
        v-if="isSelectedNumHidden == true"
        border-variant="primary"
        header="Average"
        header-border-variant="secondary"
        align="center"
        style="max-width: 10rem; max-height: 10rem"
      >
        <b-card-text v-show="this.clikedItems.length">{{
          showAverage
        }}</b-card-text>
        <b-button pill @click="resetGame">Play Again</b-button>
      </b-card>
    </div>
    <div class="select-card">
      <h4>Choose your card 👇</h4>
      <div class="button">
        <ul style="list-style-type: none">
          <li
            v-for="(numbers, index) in this.selectedNum"
            :key="numbers"
            class="button-span"
          >
            <b-button
              v-on:click="onSelect(userName, numbers)"
              variant="outline-primary"
              >{{ numbers }}</b-button
            >
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Popup from "../components/Popup.vue";
import NavBar from "../components/NavBar.vue";
import User from "../components/User.vue";
import Error from "../components/ErrorPopup.vue";

export default {
  components: { Popup, NavBar, User, Error },
  data() {
    return {
      userName: "",
      gameName: "",
      showAverage: "",
      selectedNum: [],
      clikedItems: [],
      error: false,
      hasUserSelectedNum: false,
      isSelectedNumHidden: false,
    };
  },
  created: function () {
    // Data from signup page
    const signUpdata =
      this.$route.params?.data ||
      localStorage.getItem("formData", localStorage.getItem("formData"));

    const nums = signUpdata.numberSet;
    const gameName = signUpdata.gameName;

    this.selectedNum = nums;
    this.gameName = gameName;
    this.getUserName();
  },
  methods: {
    onSelect(user, number) {
      let findUser = this.clikedItems.find((value) => {
        return value.name === user;
      });

      if (findUser) {
        findUser.number = number;
      } else {
        this.clikedItems.push({ name: user, number: number });
      }
      this.hasUserSelectedNum = true;
    },
    getUserName(name) {
      this.userName = name;
    },
    getAverage() {
      let total = 0;
      //this.showAverage = average
      if (this.hasUserSelectedNum == true) {
        for (let index = 0; index < this.clikedItems.length; index++) {
          total += this.clikedItems[index].number;
        }
        this.showAverage = total / this.clikedItems.length;
        this.isSelectedNumHidden = true;
        console.log(this.showAverage);
      } else {
        this.error = true;
      }
      //console.log(average)
    },
    resetGame() {
      this.isSelectedNumHidden = false;
      this.clikedItems[0].number = "";
      this.hasUserSelectedNum = false;
      this.error = false;
    },
    errorMessage() {
      if (this.clikedItems[0].number == "") {
        console.log("Please select a number");
      }
    },
  },
};
</script>

<style>
.container-table {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.game-table {
  border-radius: 25px;
  background: #d7e9ff;
  padding: 20px;
  width: 300px;
  height: 150px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.select-card {
  text-align: center;
  position: fixed;
  bottom: 0;
  width: 100%;
}

.button-span {
  display: inline-block;
  margin-right: 5px;
}

.user {
  width: 40%;
  height: 15px;
  position: fixed;
  top: 450px;
  right: 11.3%;
}

.average-card {
  position: absolute;
  top: 100px;
  right: 0;
  width: 200px;
  height: 500px;
}
</style>