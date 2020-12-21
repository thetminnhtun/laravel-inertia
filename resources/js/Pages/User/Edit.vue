<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
        <div class="col-6">
          <div class="card">
            <div class="card-header">Edit A User</div>
            <div class="card-body">
              <form @submit.prevent="submit" method="post">
                <div class="form-group">
                  <label>Name</label>
                  <input type="text" v-model="form.name" class="form-control" />
                </div>
                <div class="form-group">
                  <label>Email</label>
                  <input type="email" v-model="form.email" class="form-control" />
                </div>
                <div class="form-group">
                  <label>Password</label>
                  <input type="password" v-model="form.password" class="form-control" />
                </div>
                <button type="submit" class="btn btn-primary">Save</button>
              </form>
            </div>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    props: ['user'],
    data() {
        return {
            form: {
                name: this.user.name,
                email: this.user.email,
                password: null,
            }
        }
    },
    methods: {
        submit() {
            this.$inertia.put(`/user/${this.user.id}`, this.form);
        }
    }
};
</script>

<style>
</style>