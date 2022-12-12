<template>
  <input type="text" class="form-control mt-1" v-model="input" placeholder="Enter your name">
  <div v-if="errorMessage"><p style="color: red;">{{errorMessage}}</p></div>
  <button @click="getData" class="btn btn-primary btn-sm mt-1">Save</button>
  <div class="result">{{message }} {{result}}</div>
</template>

<script>
export default {
    data(){
        return {
            input: "",
            errorMessage: "",
            result: "",
            message: ""
        }
    },
    methods: {
        getData(){
            if(this.input){
                this.result = this.input
                this.input = ""
                this.message = "Welcome"
                this.errorMessage = ""
            }else{
                this.errorMessage = "Name is required!!"
                this.message = ""
                this.result = ""
            }
        }
    }
}
</script>
<style scoped>
    .result{
        margin-top: 1rem;
        border-radius: 5px;
        background-color: rgba(0, 0, 0, 0.1);
        width: 100%;
        height: 30px;
        border-left: 5px solid steelblue;    
        }
</style>