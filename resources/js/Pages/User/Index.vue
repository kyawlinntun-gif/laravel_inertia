<template>
    <div class="container mt-5">
        <div class="row">
            <div class="col-md-12">
                <!-- <h1>User List</h1> -->
                <inertia-link href="/user" class="text-decoration-none text-dark"><h1>User List</h1></inertia-link>
            </div>
            <div class="col-md-8">
                <inertia-link href="/user/create" class="btn btn-primary">Create</inertia-link>
            </div>
            <div class="col-md-4">
                <form @submit.prevent="submit">
                    <div class="input-group mb-3">
                        <input type="text" class="form-control" placeholder="Search..."
                            aria-label="Recipient's username" aria-describedby="button-addon2" v-model="q">
                        <div class="input-group-append">
                            <button class="btn btn-outline-secondary" type="submit" id="button-addon2">Search</button>
                        </div>
                    </div>
                </form>
            </div>
            <div class="col-md-12 mt-3 alert alert-success" v-if="success">
                {{ success }}
            </div>
            <div class="col-md-12 mt-4" v-if="users.data.length > 0">
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
                        <tr v-for="user in users.data" v-bind:key="user.id">
                            <td>{{ user.id }}</td>
                            <td>{{ user.name }}</td>
                            <td>{{ user.email }}</td>
                            <td>{{ user.created_at }}</td>
                            <td>
                                <inertia-link :href="`/user/${user.id}/edit`" class="btn btn-success">Edit
                                </inertia-link>
                                <button @click.prevent="destroy(user.id)" class="btn btn-danger">Delete</button>
                            </td>
                        </tr>
                    </tbody>
                </table>

                <nav aria-label="Page navigation example">
                    <ul class="pagination">
                        <li v-for="(link, index) in users.links" v-bind:key="index"
                            :class="['page-item', link.url !== null ? link.url : 'disabled', link.active ? 'active' : '']">
                            <inertia-link class="page-link" :href="link.url !== null ? link.url : '#'"
                                v-html="link.label"></inertia-link>
                        </li>
                    </ul>
                </nav>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Index',
        props: ['users', 'success', 'search'],
        data() {
            return {
                q: this.search ? this.search : ''
            }
        },
        methods: {
            destroy(id) {
                this.$inertia.delete(`/user/${id}`);
            },
            submit() {
                this.$inertia.get(`/user?search=${this.q}`)
            }
        }
    }

</script>

<style>

</style>
