<template>
    <div class="container mt-5">
        <div class="row justify-content-center">
            <div class="col-md-6">
                <h3>Create A User</h3>
                <form @submit.prevent="submit">
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input type="text" id="name" class="form-control" v-model="form.name">
                    </div>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" id="email" class="form-control" v-model="form.email">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" id="password" class="form-control" v-model="form.password">
                    </div>
                    <div class="form-group">
                        <button type="submit" class="btn btn-primary">Create</button>
                        <inertia-link href="/user" class="btn btn-secondary float-end">Back</inertia-link>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Create',
    data() {
        return {
            form: {
                name: '',
                email: '',
                password: ''
            }
        }
    },
    methods: {
        submit() {
            this.$inertia.post('/user/', this.form);
        }
    }
}
</script>

<style>

</style>
