<template>
  <form action="">
    <select name="selectMethod" id="" v-model="input">
      <option value="Get">GET</option>
    </select>
    <input type="url" v-model="inputs.apiUrl" />
    <button type="submit" @click="Send">Send</button>
  </form>
  <div>
    <div class="my-3" id="responseJsonBox">
      <div class="form-group row">
        <label for="responseJsonText" class="col-sm-2 col-form-label"
          >Response</label
        >

        <textarea
          name="response"
          id="response"
          cols="30"
          rows="10"
          v-model="listDataString"
        >
        </textarea>
        
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      inputs: {
        httpmethod: "",
        apiUrl: "",
      },
      listDataString: String,
      Response: [],
    };
  },

  methods: {
    async Send(e) {
      e.preventDefault();
      const response = await axios.get(
       this.inputs.apiUrl
      );
      this.listDataString = JSON.stringify(response.data, null, "\t");
      
      this.Response = response.data;
      console.log(this.Response);
    },
  },
};
</script>

<style>
</style>