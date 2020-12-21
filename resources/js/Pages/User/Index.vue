<template>
  <div class="container">
      <div class="my-5">
          <a href="/user/create" class="btn btn-primary">Create</a>
      </div>
      <table class="table">
        <thead>
          <tr>
            <td>ID</td>
            <td>Name</td>
            <td>Email</td>
            <td>Date</td>
            <td>Actions</td>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in users" :key="user.id">
            <td>{{ user.id }}</td>
            <td>{{ user.name }}</td>
            <td>{{ user.email }}</td>
            <td>{{ user.created_at }}</td>
            <td>
              <a :href="`/user/${user.id}/edit`" class="btn btn-success">Edit</a>
              <button @click="destroy(user.id)" class="btn btn-danger">Delete</button>
            </td>
          </tr>
        </tbody>
      </table>
  </div>
</template>

<script>
export default {
    props: ['users'],
    methods: {
        destroy(id) {
            if(confirm('Are you sure to delete?')) {
                this.$inertia.delete(`/user/${id}`)
            }
        }
    }
}
</script>

<style>

</style>