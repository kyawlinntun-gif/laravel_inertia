<template>
    <div class="container mt-5">
        <div class="row">
            <div class="col-md-12">
                <h1>User List</h1>
                <inertia-link href="/user/create" class="btn btn-primary">Create</inertia-link>
            </div>
            <div class="col-md-12 mt-3 alert alert-success" v-if="success">
                {{ success }}
            </div>
            <div class="col-md-12 mt-4" v-if="users.length > 0">
                <table class="table">
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Name</th>
                            <th>Email</th>
                            <th>Date</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="user in users" v-bind:key="user.id">
                            <td>{{ user.id }}</td>
                            <td>{{ user.name }}</td>
                            <td>{{ user.email }}</td>
                            <td>{{ user.created_at }}</td>
                            <td>
                                <a href="#" class="btn btn-success">Edit</a>
                                <button @click.prevent="destroy(user.id)" class="btn btn-danger">Delete</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Index',
    props: ['users', 'success'],
    methods: {
        destroy(id) {
            this.$inertia.delete(`/user/${id}`);
        }
    }
}
</script>

<style>

</style>
