<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3 v-if="city!==''">{{ city }}</h3>
    <center v-else>
      <b-form-group
        style="width: 200px"
        id="fieldset-1"
        label="Enter your zipcode"
        label-for="input-1"
        valid-feedback="Thank you!"
        :invalid-feedback="invalidFeedback"
        :state="state"
      >
        <b-form-input
          id="input-1"
          v-model="name"
          :state="state"
          trim
        ></b-form-input>
      </b-form-group>
      <b-button
        style="margin-top: 10px"
        variant="primary"
        v-on:click="searchZip"
      >
        Search
      </b-button>
    </center>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Zip_Details",
  props: {
    msg: String,
  },
  data() {
    return {
      city: "LOS ANGELES, CA",
    };
  },
  methods: {
    searchZip: async function () {
      const field = document.querySelector("input[id=input-1]").value;
      axios
        .get(
          `https://api.zip-codes.com/ZipCodesAPI.svc/1.0/QuickGetZipCodeDetails/${field}?key=DEMOAPIKEY`
        )
        .then((response) => {
          response.data.City && (this.city = response.data.City+","+response.data.State);
        })
        .catch((e) => {
          console.log("Error", e.toString());
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
