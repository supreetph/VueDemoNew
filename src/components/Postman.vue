<template>
  <form action="">
      <select name="selectMethod" id="" v-model="input">
          <option value="Get">GET</option>
      </select>
      <input type="url" v-model="inputs.apiUrl">
      <button type="submit" @click="Send">Send</button>
  </form>
  <div>
    <div class="my-3" id="responseJsonBox">
                <div class="form-group row">
                    <label for="responseJsonText" class="col-sm-2 col-form-label">Response</label>
                    <div class="col-sm-10">
                        <!-- <textarea class="form-control" id="responseJsonText" rows="3">Your response will appear here</textarea> -->

                        // <pre id='responsePre' class="language-javascript"> <code id='responsePrism' class="language-javascript"> {{Response}} </code> </pre>
                    </div>
                </div>
            </div>

    
  </div>
</template>

<script>
import axios from 'axios'
export default {
data(){
    return{
        inputs:{
            httpmethod:'',
            apiUrl:''
        },
        Response:[]
    }

},

    methods:{
      async Send(e){
           e.preventDefault();
          const response= await axios.get('https://jsonplaceholder.typicode.com/todos/1')
          console.log(response.data);
          this.Response=response.data
           
       } 
    }


}
</script>

<style>

</style>