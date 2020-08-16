<template>
  <div class="d-flex flex-row">
    <form class="d-flex flex-column w-50">
      <div class="form-group">
        <label>Email address</label>
        <input novalidate="true" type="email" class="form-control" placeholder="Enter email">
      </div>  
      <div class="form-group">
        <label>Password</label>
        <input type="password" class="form-control" placeholder="Password">
      </div>
      <div class="form-group">
        <label>Age</label>
        <input type="number" class="form-control" placeholder="Age">
      </div>
      <div class="form-group">
        <label>Size</label>
        <select class="form-control">
          <option>Petit</option>
          <option>Moyen</option>
          <option>Grand</option>
        </select> 
      </div>
      <div class="form-check">
        <input class="form-check-input" type="radio" name="gender"  value="man" >
        <label class="form-check-label">Homme</label>
      </div>
      <div class="form-check">
        <input class="form-check-input" type="radio" name="gender" value="woman">
        <label class="form-check-label">Femme</label>
      </div>
      <div class="form-group form-check">
        <input type="checkbox" class="form-check-input">
        <label class="form-check-label" for="gender">Recevoir des pubs</label>
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
    <div class="w-50 d-flex flex-row justify-content-center align-items-center">
      <pre>{{ $data }}</pre>
    </div>
  </div>
</template>

<script>
export default {
  name: 'my-form',
  data() {
    return {

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
