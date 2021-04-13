<template>
  <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-text-field
      v-model="username"
      :counter="10"
      label="username"
      required
    ></v-text-field>

    <v-text-field
      v-model="password"
      label="password"

      required
    ></v-text-field>

    <v-btn
      :disabled="!valid"
      class="mr-4"
      @click="validate"
    >
      로그인 하기!
    </v-btn>

  </v-form>
</template>
<script>
import axios from 'axios';
  export default {
    data: () => ({
      valid: true,
      username: '',
    
      "nickname": "",
      "password": "",
       checkbox: false,
    }),

    methods: {
      validate () {

    axios({
              method: "POST",
              url:'http://172.20.10.2:8000/user/login/',
              data:{
                  username:this.username,
                  password:this.password
              }
          }).then((c)=>{
              console.log(c)
          })
          .catch(()=>{
              console.log(this.username,this.nickname,this.password)
          })

        },
 
    },
  }
</script>