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
      v-model="nickname"
      label="Nickname"
      required
    ></v-text-field>

    <v-text-field
      v-model="password"
      label="password"
          required
    ></v-text-field>

    <v-text-field
      v-model="check_password"
      label="check_password"
      required
    ></v-text-field>

    <v-checkbox
      v-model="checkbox"
      :rules="[v => !!v || 'You must agree to continue!']"
      label="Is Jong geon your god?"
      required
    ></v-checkbox>

    <v-btn
      :disabled="!valid"
      class="mr-4"
      @click="validate"
    >
      회원가입하기!
    </v-btn>

  </v-form>
</template>
<script>
import axios from 'axios';
  export default {
    data: function(){
        return{
      valid: true,
      username: '',
      password: '', 
    check_password: '', 
    nickname:'',

      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      checkbox: false,
        }
    },

    methods: {
      validate () {
          axios({
              method: "POST",
              url:'http://172.20.10.2:8000/user/register/',
              data:{
                  username:this.username,
                  nickname:this.nickname,
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