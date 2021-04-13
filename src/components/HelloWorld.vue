<template>
    <div class="temp">
      <p>
        <input type="button" v-on:click="relocate('Seoul')" value="Seoul" />
        <input type="button" v-on:click="relocate('Cheonan')" value="Cheonan" />
        <input type="button" v-on:click="relocate('Asan')" value="Asan" />
        <input type="button" v-on:click="relocate('Daejeon')" value="Daejeon" />
        <input type="button" v-on:click="relocate('Andong')" value="Andong" />
      </p>
      <div class="temperature">    
        <div>
          {{location}}의 평균 온도는 {{TE}}°C   
        </div>
        <div>
          최저 온도는 {{MIN_TE}}°C
        </div>
        <div>
          최저 온도는 {{MAX_TE}}°C
        </div>
        <div>
          습도는 {{hum}}%
        </div>

      </div>
    </div>
</template>

<script>
// import Login from './login';
import axios from 'axios';
export default {
  name: 'HelloWorld',
  props: {
    
  },
    data: function(){
      return{
       TE: '',
       MAX_TE:'',
       MIN_TE:'',
       hum:'', // 습도
       d:'',
       location:'Seoul'
      }
  },
  created:function(){
    this.get_temp();
  },
  
  methods:{
  
      get_temp: function() {
         this.d = axios.get(`http://api.openweathermap.org/data/2.5/weather?q=${this.location}&appid=e286dab9eb8ef5f640822dc78093df25`).then((e)=>{
           this.TE = Math.round(e.data.main.temp - 273);
           this.MAX_TE = Math.round(e.data.main.temp_max - 273);
           this.MIN_TE = Math.round(e.data.main.temp_min - 273);
           this.hum = e.data.main.humidity;
                    })
        },
          relocate: function(l){
           this.location = l;
           console.log(this.location);
                    this.d = axios.get(`http://api.openweathermap.org/data/2.5/weather?q=${this.location}&appid=e286dab9eb8ef5f640822dc78093df25`).then((e)=>{
                      console.log(e.data.main);
           this.TE = Math.round(e.data.main.temp - 273);
           this.MAX_TE = Math.round(e.data.main.temp_max - 273);
           this.MIN_TE = Math.round(e.data.main.temp_min - 273);
           this.hum = e.data.main.humidity;


         })
           
         }
      
  }

  //components:{Login}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.temperature {
  font-size: 5rem;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
p {
  display:flex;
  justify-content: space-around;
  
}
input {
  padding: 30px;
  background-color: aqua;
  border-radius: 30px;
}
</style>
