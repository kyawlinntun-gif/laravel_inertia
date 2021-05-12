<template>
    <div class="container mt-5">
        <div class="row justify-content-center">
            <div class="col-md-6">
                <h3>Create A User</h3>
                <UserForm :user="user" :errors="errors" v-on:submit="submit" ></UserForm>
            </div>
        </div>
    </div>
</template>

<script>
import UserForm from './UserForm';

export default {
  components: { UserForm },
    name: 'Create',
    props: ['user','errors'],
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
        submit(form) {
            this.$inertia.post('/user/', form);
        }
    }
}
</script>

<style>

</style>
