<template>
  <div class="d-flex flex-row">
    <form @submit="submitForm" class="d-flex flex-column w-50">
      <div class="form-group">
        <label>Email address</label>
        <input v-model.trim="form.email" novalidate="true" type="email" class="form-control" placeholder="Enter email">
      </div>  
      <div class="form-group">
        <label>Password</label>
        <input v-model.trim="form.password" type="password" class="form-control" placeholder="Password">
      </div>
      <div class="form-group">
        <label>Age</label>
        <input v-model.lazy.number="form.age" type="number" class="form-control" placeholder="Age">
      </div>

      <idea v-model="form.idea"></idea>

      <div class="form-group">
        <label>Size</label>
        <select v-model="form.size" class="form-control">
          <option>Petit</option>
          <option>Moyen</option>
          <option>Grand</option>
        </select> 
      </div>
      <div class="form-check">
        <input v-model.trim="form.gender" class="form-check-input" type="radio" name="gender"  value="man" >
        <label class="form-check-label">Homme</label>
      </div>
      <div class="form-check">
        <input v-model.trim="form.gender"  class="form-check-input" type="radio" name="gender" value="woman">
        <label class="form-check-label">Femme</label>
      </div>
      <div class="form-group form-check">
        <input v-model="form.ads" type="checkbox" class="form-check-input">
        <label class="form-check-label" for="gender">Recevoir des pubs</label>
      </div>

      <ul v-if="errors.length" class="card alert-danger">
        <li v-for="error in errors" :key="error"> {{ error }} </li>
      </ul>

      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
    <div class="w-50 d-flex flex-row justify-content-center align-items-center">
      <pre>{{ $data }}</pre>
    </div>
  </div>
</template>

<script>
import Idea from './Idea.vue';

export default {
  name: 'my-form',
  components: {
    Idea,
  },
  data() {
    return {
      form: {
        email: 'john@gmail.com',
        password: '123456',
        age: 18,
        size: 'Moyen',
        gender: 'man',
        ads: false,
        idea: true,
      },
      errors: []
    }
  },
  methods: {
    submitForm(event) {
      event.preventDefault();

      this.verifyForm().then( () => {
        console.log( {...this.form} );
      }).catch( () => {
        console.log( this.errors )
      } )
    },
    verifyForm() {
      this.errors = [];

      return new Promise( (resolve, reject) => {

        setTimeout( () => {

          if(!this.form.password) {
            this.errors.push('Password missing');
          }

          if(this.form.password && this.form.password.length < 6) {
            this.errors.push('Password should be at least 6 characters');
          }

          this.errors.length ? reject('ko') : resolve('ok');
        }, 3000 )
        
      } );

    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
