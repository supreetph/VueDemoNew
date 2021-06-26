<template>
<h1>SupaMan</h1>
  <form action="">
    <select name="selectMethod" id="" v-model="inputs.httpmethod">
      <option value="Get">GET</option>
      <option value="Post">POST</option>
    </select>
    <input type="url" v-model="inputs.apiUrl" />
    <button type="submit" @click="Send" class="bt">Send</button><br /><br />
    <label for="request">Request Body</label>
    <textarea v-model="inputs.body">Request Body</textarea>
  </form>
  <div>
    <div class="my-3" id="responseJsonBox">
      <div class="form-group row">
        Status: <label for="status">{{ ResposneMetadata.status }}</label
        ><br />
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
        body: {},
      },
      listDataString: String,
      Response: [],
      ResposneMetadata: {
        status: 0,
      },
    };
  },

  methods: {
    async Send(e) {
      e.preventDefault();

      if (this.inputs.httpmethod === "Get") {
        const response = await axios.get(this.inputs.apiUrl);
        this.listDataString = JSON.stringify(response.data, null, "\t");

        this.Response = response.data;
        console.log(this.Response);
      } else {
        e.preventDefault();
        var data = JSON.stringify(this.inputs.body);
        console.log(data);
        var result = await axios.post(
          "https://reqres.in/api/users",
          this.inputs.body
        );

        console.log(result.data);
        console.log(result.status);
        this.ResposneMetadata.status = result.status;
        console.log(result.headers);
        this.listDataString = JSON.stringify(result.data, null, "\t");
      }
    },
  },
};
</script>

<style>
</style>