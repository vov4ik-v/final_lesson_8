<template>
  <div class="container column">
      <app-select :values="values" @block-added="addBlock"></app-select>
      <app-view :values="values"></app-view>
  </div>
  <div class="container">
    <app-loader v-if="showLoader"></app-loader>
    <app-comments v-else :comments="comments" @load-comments="loadComments"></app-comments>
  </div>
</template>

<script>
  import AppSelect from "./components/AppSelect";
  import AppTeg from "./components/AppTeg";
  import AppLoader from "./components/AppLoader"
  import AppView from "./components/AppView";
  import axios from 'axios';
  import AppComments from "./components/AppComments";


export default {
  data() {
    return {
      comments:[],
      showLoader:false,
      values:[],

    }
  },
  methods:{
    addBlock(block){
      this.values.push(block)
    },
    async loadComments(){
      this.showLoader = true
      const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = Object.keys(data).map(key =>{
        return{
          id:data[key].id,
          nickname: data[key].email,
          body: data[key].body
        }
      })
      this.showLoader = false


    }
  },
  components:{
    AppComments,
    AppSelect,AppTeg,AppLoader,AppView
  },

}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
