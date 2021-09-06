<template>
  <div class="sign-form">
    <h3>Create a Game 👾</h3>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group id="input-group-2" label="Game Name" label-for="input-2">
        <b-form-input
          id="input-1"
          v-model="form.gameName"
          placeholder="Game's name"
          required
        ></b-form-input>
      </b-form-group>
       <b-form-group id="input-group-3" label="Voting System:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.numberSet"
          :options="set"
          required
        ></b-form-select>
      </b-form-group>
      <b-form-group id="input-group-3" label="Who can show cards?" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.showCard"
          :options="showOption"
          required
        ></b-form-select>
      </b-form-group>
      <br>
      <div class="buttons">
        <b-button type="submit" variant="primary">Submit</b-button>
        <b-button type="reset" variant="secondary">Reset</b-button>
      </div>
    </b-form>
  </div>
</template>

<script>
//import io from 'socket.io-client';

export default {
    name: 'Signup',
    data() {
        return {
            form: {
                gameName: '',
                numberSet: null,
                showCard: null,
            },
            set: [
                    {text: 'Select One', value: null}, 
                    {text: "Fibonacci: (0, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, '?')", value: [0,1,2,3,5,8,13,21,34,55,89,'?']},
                    {text: "Modified Fibonacci: (0, '½', 1, 2, 3, 5, 8, 13, 20, 40, 100, '?')", value: [0, 0.5, 1, 2, 3, 5, 8, 13, 20, 40, 100, '?']}, 
                ],
            showOption: 
                [
                    {text: 'Select One', value: null},
                    {text: "Only me", value: false},
                    {text: "Everyone", value: true}
                ],
            show: true
        }
    },
    methods: {
        onSubmit(event) {
            event.preventDefault()
            // alert(JSON.stringify(this.form)) //shows in browser as an alert
            localStorage.setItem('formData',this.form)
            this.$router.push({ name: 'game', params: { data: this.form } })
        },
        onReset(event) {
            event.preventDefault()
            this.form.gameName = '',
            this.form.numberSet = null
            this.form.showCard = null

            //Clear native browser form validation state
            this.show = false
            this.$nextTick(() =>{
                this.show = true
            })
        }
    }
}
</script>

<style>

.sign-form {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

</style>