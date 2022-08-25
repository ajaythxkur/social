<template>
    <div>
        <div class="main-parent d-flex align-items-center">
            <div class="container">
                <div class="row">
                    <div class="col-12 col-md-12 col-lg-12">
                        <div class="admin-login d-flex justify-content-center">
                            <form class="admin-login-form w-25 border rounded p-3 text-center" @submit="onSubmit">
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="name-icon"><img src="@/assets/icons/Admin/name.svg" alt="name" class="img-fluid"></span>
                                    <input v-model="fname" type="text" class="form-control" placeholder="First Name" aria-label="First Name" aria-describedby="name-icon">
                                    <div v-if="v$.errors">error</div>
                                </div>
                                {{ v$.$errors }}
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="name-icon"><img src="@/assets/icons/Admin/name.svg" alt="name" class="img-fluid"></span>
                                    <input v-model="lname" type="text" class="form-control" placeholder="Last Name" aria-label="Last Name" aria-describedby="name-icon">
                                </div>
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="user-icon"><img src="@/assets/icons/Admin/user.svg" alt="user" class="img-fluid"></span>
                                    <input v-model="username" type="text" class="form-control" placeholder="Username" aria-label="Username" aria-describedby="user-icon">
                                </div>
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="envelope-icon"><img src="@/assets/icons/Admin/envelope.svg" alt="envelope" class="img-fluid"></span>
                                    <input v-model="email" type="text" class="form-control" placeholder="Email Address" aria-label="Email Address" aria-describedby="envelope-icon">
                                </div>
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="lock-icon"><img src="@/assets/icons/Admin/lock.svg" alt="envelope" class="img-fluid"></span>
                                    <input v-model="password" type="password" class="form-control" placeholder="Password" aria-label="Password" aria-describedby="lock-icon">
                                </div>
                                <div class="mb-3">
                                    <label for="gender">Male&nbsp;</label>
                                    <input v-model="gender" type="radio" name="gender" value="" checked>
                                    <label for="gender">Female&nbsp;</label>
                                    <input v-model="gender" type="radio" name="gender" value="">
                                </div>
                                <input type="submit" value="Sign Up" class="btn btn-outline-light">
                            </form>
                        </div>
                        <!-- admin-login-form -->
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import useVuelidate from '@vuelidate/core'
import { required } from '@vuelidate/validators'
export default{
    name: 'AdminLogin',
    setup(){
        return { v$: useVuelidate() }
    },
    data(){
        return{
            fname: '',
            lname: '',
            username: '',
            email: '',
            password: '',
            gender: ''
        }
    },
    validations() {
        return {
            fname: { required },
            lname: { required },
            username: { required },
            email: { required },
            password: { required }
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault();
            let formCheck = this.v$.$validate()
            console.log(formCheck)
            if(!formCheck) return
        }
    }
}
</script>
<style>
.main-parent {
    min-height: 100vh;
}
.admin-login-form .input-group .input-group-text {
    background-color: var(--ln-black);
}
.admin-login-form .input-group input{
    background-color: var(--ln-black);
    color: var(--ln-gray);
}
.admin-login-form .input-group input:focus{
    border-color: var(--ln-gray);
    box-shadow: none;
}
.admin-login-form .input-group input::placeholder{
    color: var(--ln-gray);
}
</style>