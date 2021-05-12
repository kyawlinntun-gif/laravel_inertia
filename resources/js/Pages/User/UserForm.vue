<template>
    <form @submit.prevent="submit">
        <div class="form-group">
            <label for="name">Name</label>
            <input type="text" id="name" class="form-control" v-model="form.name" :class="{'is-invalid': errors.name}">
            <div class="invalid-feedback" v-if="errors.name">{{ errors.name }}</div>
        </div>
        <div class="form-group">
            <label for="email">Email</label>
            <input type="email" id="email" class="form-control" v-model="form.email" :class="{'is-invalid' : errors.email}">
            <div class="invalid-feedback" v-if="errors.email">{{ errors.email }}</div>
        </div>
        <div class="form-group">
            <label for="password">Password</label>
            <input type="password" id="password" class="form-control" v-model="form.password" :class="{'is-invalid' : errors.password}">
            <div class="invalid-feedback" v-if="errors.password">{{ errors.password }}</div>
        </div>
        <div class="form-group">
            <button type="submit" class="btn btn-primary" v-if="user.id">Update</button>
            <button type="submit" class="btn btn-primary" v-else>Create</button>
            <inertia-link href="/user" class="btn btn-secondary float-end">Back</inertia-link>
        </div>
    </form>
</template>

<script>
export default {
    name: 'UserForm',
    props: ['user', 'errors'],
    data() {
        return {
            form: {
                name: this.user.name,
                email: this.user.email,
                password: ''
            }
        }
    },
    methods: {
        submit()
        {
            this.$emit('submit', this.form);
        }
    }
}
</script>

<style>

</style>
