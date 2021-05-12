<template>
    <div class="container mt-5">
        <div class="row justify-content-center">
            <div class="col-md-6">
                <h3>Edit A User</h3>
                <UserForm :user="user" :errors="errors" v-on:submit="submit" ></UserForm>
            </div>
        </div>
    </div>
</template>

<script>
import UserForm from './UserForm.vue';

export default {
    components: {
        UserForm
    },
    name: 'Create',
    props: ['user', 'errors'],
    methods: {
        submit(form) {
            this.$inertia.put(`/user/${this.user.id}`, form);
        }
    }
}
</script>

<style>

</style>
