<template>
  <div class="dashboard">
      <h1> Welcome on dashboard</h1>
      <v-btn @click="signout">Sign Out</v-btn>
  </div>
</template>

<script>
import firebase from 'firebase';
export default {
  data(){
    return{
      username:[]
    }
  },
  
  methods:{
    async signout(){
      try{
           const data=await firebase.auth().signOut();
      console.log(data);
       this.$router.replace({ name: "Home" });
      }catch(err){
        console.log(err);
      }
    }
  }
}
</script>

<style>

</style>