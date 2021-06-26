<template>
  <h1>SupaMan</h1>
  <form action="">
    <div class="mb-3 col-sm-3">
      <select
        name="selectMethod"
        class="form-select"
        
        id=""
        v-model="inputs.httpmethod"
      >
        <option value="Get" selected>GET</option>
        <option value="Post">POST</option>
      </select>
    </div>
    <div class="input-group" col-sm-8 >
      <span class="input-group-text" id="addon-wrapping"
        >https://example.com/users/</span
      >
      <input
        type="text"
        class="form-control"
        id="basic-url"
        aria-describedby="addon-wrapping"
        v-model="inputs.apiUrl"
        width="50%"
      />
    </div>
<div class="container"></div>
    <button type="submit" @click="Send" class="btn btn-primary">Send</button
    ><br /><br />
    <div class="input-group">
      <span class="input-group-text">Request Body</span>

      <textarea v-model="inputs.body" class="form-control">
Request Body</textarea
      >
    </div>
  </form>
  <div>
    <div class="my-3" id="responseJsonBox">
      <div class="form-group row col-sm-1">
        <br /><button type="button" class="btn btn-primary">
          Status
          <span class="badge bg-secondary">{{ ResposneMetadata.status }}</span>
        </button>

        <div class="form-floating mb-3">
          <textarea
            name="response"
            id="response"
            cols="30"
            rows="10"
            v-model="listDataString"
          >
          </textarea>
          <label for="response">Response</label>
        </div>
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
      listDataString: '',
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