<template>
    <div class="container">
        <form>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <div class="panel panel-default">
                     <div class="panel-heading">
                        <h4>The form</h4>
                     </div>
                     <div class="panel-body">
                       <name-control v-model="name"></name-control>
                       <div class="form-group">
                        <label for="appvi2">Email: </label>
                        <input id="appvi2" type="email" v-model="email">
                       </div>
                       <div class="form-group">
                        <label for="appvi3">Password: </label>
                        <input id="appvi3" type="password" v-model="password">
                       </div>
                       <div class="form-group">
                        <input type="checkbox" id="appvc1" value="yes" v-model="storedInBase">
                        <label for="appvc1">Store in database?</label>
                       </div>
                      <button class="btn btn-primary" @click.prevent="checkAndUnveil()">Submit</button>
                     </div>
                    </div>
                </div>
            </div>
        </form>
        <hr>
        <div class="row" v-show="!hidden">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body">
                        <p>Full Name: {{name.givenName}} {{name.familyName}}</p>
                        <p>Mail: {{email}}</p>
                        <p>Password: {{password}}</p>
                        <p>Store in Database: {{storedInBase.length?"YES":"NO"}}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import nameControl from "./components/NameControl.vue"
    export default {
        data() {return({
            name: {givenName: "", familyName: ""},
            email: "",
            password: "",
            // note: this property below could simply be a boolean instead of an array
            //       because its connected checkbox has no other connection to make
            //       a 'group' of checkboxes whose values accumulate in the array
            storedInBase: [],
            hidden: true});},
        methods: {
         checkAndUnveil() {
             if(this.name.familyName.length && this.email.length && this.password.length) {
              this.hidden=false;
              // note: just for fun, hides again after a few seconds
              //       it is worth noticing 'this' refers to the Vue object because of arrow function
              setTimeout(() => {
                this.hidden=true;
              }, 5000);
             }
          }
        },
        components: {
         nameControl
        }
    }
</script>

<style scoped>
</style>
