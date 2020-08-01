<template>
    <div>
        <v-btn text color="white" @click="dialog=true">
              <span class="mr-2">Login</span>
                  <v-icon color="white" >mdi-logout</v-icon>
                 </v-btn>
         <v-dialog v-model="dialog" max-width="500px">
            <v-card class="pa-4 rounded-xl white--text" color="rgba(255,255,255,0.5)">
            <div class="login-popup">
            <v-card-title class="display-2">Login</v-card-title>

            <v-text-field v-model="username" label="Username" color="black">
            </v-text-field>
            <v-text-field v-model="password" type="password" label="Password" color="black">
            </v-text-field>
            <v-btn @click="submit" class="success">Submit</v-btn>
            </div>
            </v-card>
        </v-dialog>
    </div>
</template>
<script>
import firebase from 'firebase';

export default {
    data(){
        return{
            username:"",
            password:"",
            dialog:false,
        }
    },
    methods:{
        submit(){
            console.log(this.username)
            firebase.auth().signInWithEmailAndPassword(this.username,this.password)
            .then(user=>{
                console.log("logged in")
                console.log(user)
                this.dialog=false;
                this.$router.replace({ name: "Dashboard" });
            },
          err => {
            alert(err.message);
          }
            )
        }
        
    }
}
</script>
<style scoped>
.login-popup{
    color: black;
    font-family: Georgia, 'Times New Roman', Times, serif;
}
</style>