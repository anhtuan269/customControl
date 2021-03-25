<template>
  <div class="container">
    <form action="#">
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
          <h1 class="text-center">Form Section For Sky ALbert</h1>
          <hr />
          <div class="mb-3">
            <label for="email" class="form-label"> Mail</label>
            <input
              type="text"
              id="email"
              class="form-control"
              :value=" userData.email "
              @input=" userData.email = $event.target.value"
            />
          </div>
          <div class="form-group mb-3">
            <label for="password" class="form-label"> Password</label>
            <input 
              type="password" 
              id="password" 
              class="form-control"
              v-model="userData.password"
               />
          </div>
          <div class="form-group mb-3">
            <label for="age" class="form-label">Age</label>
            <input 
              type="number" 
              id="age"
              class="form-control"
              v-model="userData.age"
               />
          </div>
        </div>
      </div>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
          <label for="message" class="form-label"> Message</label>
          <br />
          <textarea 
            class="form-control" 
            id="message"
            rows="5"
            v-model="message"
            ></textarea>
        </div>
      </div>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
          <div class="form-group">
            <label for="sendmail">
              <input 
                type="checkbox" 
                id="sendmail" 
                value="SendMail"
                v-model="sendEmail"
                 /> Sen Mail
            </label>
            <label for="sendInfomail">
              <input 
                type="checkbox" 
                id="sendInfomail" 
                value="SendInfomail"
                v-model="sendEmail"
                 />
              SendInfomail
            </label>
          </div>
        </div>
      </div>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
          <label for="male">
            <input 
              type="radio" 
              id="male" 
              value="Male" 
              v-model="gender"
              /> Male
          </label>
          <label for="female">
            <input 
              type="radio" 
              id="female" 
              value="Female"
              v-model="gender"
               /> Female
          </label>
        </div>
      </div>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
          <label for="priority"> Priority</label>
          <select 
          id="priority" 
          class="form-control"
          v-model="selected"
          >
            <option 
              v-for="(priority, index) in priorities" :key="index" 
              :value="index"
              @click="this.showIndex = $event.target.value"
              :selected=" priority == 'medium'"
              > 
              {{priority}}</option>
          </select>
          <hr />
        </div>
      </div>
       <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
        <label for="switched" > Switched: </label>
          <Customcontrol
          :value="dataSwitch"
          @input="dataSwitch = $event "
           v-model="dataSwitch"
          >
           </Customcontrol>
        </div>
      </div>
      <div class="row">
        <div
          class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
        >
          <button 
          class="btn btn-primary" 
          @click.prevent="submit"
          >
          Submit!</button>
        </div>

      </div>
    </form>
    <div 
      class="row"
      v-if="isSubmit"
      >
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <hr />
        <div class="panel panel-default">
          <div class="panel-heading">
            <h4>Your Data</h4>
          </div>
          <div class="panel-body">
            <p>Mail: {{ userData.email }}</p>
            <p>Password: {{userData.password}}</p>
            <p>Age: {{userData.age}}</p>
            <p
              style="white-space: pre"
            >
              Message: {{message }}
            </p>
            <p><strong> Send Mail?</strong></p>
            <ul>
              <li
              v-for="(item, index) in sendEmail" :key="index"
              >
              {{item}}
              </li>
                <p>Gender: {{gender}}</p>
                <p>Priority: {{priorities[selected]}} </p>
                <p>Swithed: {{dataSwitch}}</p>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Customcontrol from './components/Customcontroll.vue';
export default {
  name: "App",
  data() {
    return {
      userData: {
        email:'Admin',
        age: 16,
        password:'123456'
      },
      message: 'this is messsage',
      sendEmail:[],
      gender:'Male',
      priorities:[
        'High','Medium','Low'
      ],
      dataSwitch:true,
      showIndex:1,
      isSubmit:false,
      selected:''

    };
  },
  components: { 
    Customcontrol
  },
  methods: {
    show(index){
      this.showIndex = index;
      console.log(index);
    },
    submit(){
      this.isSubmit = true;
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app .row {
  justify-content: center;
  text-align: left;
}
</style>
