<template>
    <div>
        <div class="main-parent d-flex align-items-center">
            <div class="container">
                <div class="row">
                    <div class="col-12 col-md-12 col-lg-12">
                        <div class="admin-login d-flex justify-content-center">
                            <form class="admin-login-form border rounded p-3 text-center" @submit.prevent="onSubmit"
                                v-if="loading" autocomplete="off">
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="name-icon"><img
                                            src="@/assets/icons/Admin/sign.svg" alt="name" class="img-fluid"></span>
                                    <input v-model="fname" type="text" class="form-control" placeholder="First Name"
                                        aria-label="First Name" aria-describedby="name-icon">
                                </div>
                                <div class="text-danger mb-3" v-for="error in v$.fname.$errors" :key="error.$uid">
                                    {{ error.$message }}
                                </div>
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="name-icon"><img
                                            src="@/assets/icons/Admin/sign.svg" alt="name" class="img-fluid"></span>
                                    <input v-model="lname" type="text" class="form-control" placeholder="Last Name"
                                        aria-label="Last Name" aria-describedby="name-icon">
                                </div>
                                <div class="text-danger mb-3" v-for="error in v$.lname.$errors" :key="error.$uid">
                                    {{ error.$message }}
                                </div>
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="user-icon"><img
                                            src="@/assets/icons/Admin/user.svg" alt="user" class="img-fluid"></span>
                                    <input v-model="username" type="text" class="form-control" placeholder="Username"
                                        aria-label="Username" aria-describedby="user-icon">
                                </div>
                                <div class="text-danger mb-3" v-for="error in v$.username.$errors" :key="error.$uid">
                                    <span>{{ error.$message }}</span>
                                </div>
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="envelope-icon"><img
                                            src="@/assets/icons/Admin/envelope.svg" alt="envelope"
                                            class="img-fluid"></span>
                                    <input v-model="email" type="text" class="form-control" placeholder="Email Address"
                                        aria-label="Email Address" aria-describedby="envelope-icon">
                                </div>
                                <div class="text-danger mb-3" v-for="error in v$.email.$errors" :key="error.$uid">
                                    <span>{{ error.$message }}</span>
                                </div>
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="lock-icon"><img
                                            src="@/assets/icons/Admin/lock.svg" alt="envelope" class="img-fluid"></span>
                                    <input v-model="password" type="password" class="form-control"
                                        placeholder="Password" aria-label="Password" aria-describedby="lock-icon">
                                </div>
                                <div class="text-danger mb-3" v-for="error in v$.password.$errors" :key="error.$uid">
                                    <span>{{ error.$message }}</span>
                                </div>
                                <div class="input-group mb-3">
                                    <span class="input-group-text" id="lock-icon"><img
                                            src="@/assets/icons/Admin/lock.svg" alt="envelope" class="img-fluid"></span>
                                    <input v-model="confirm_password" type="password" class="form-control"
                                        placeholder="Confirm Password" aria-label="Confirm Password"
                                        aria-describedby="lock-icon">
                                </div>
                                <div class="text-danger mb-3" v-for="error in v$.confirm_password.$errors"
                                    :key="error.$uid">
                                    <span>{{ error.$message }}</span>
                                </div>
                                <div class="mb-3">
                                    <label for="gender">Female&nbsp;</label>
                                    <input v-model="gender" type="radio" name="gender" value="">&nbsp;
                                    <label for="gender">Male&nbsp;</label>
                                    <input v-model="gender" type="radio" name="gender" value="">
                                </div>
                                <input type="submit" value="Sign Up" class="btn btn-outline-light">
                            </form>
                            <form class="admin-login-form w-25 border rounded p-3 text-center" @submit="onSubmit"
                                v-else>
                                <Skeletor width="100%" height="30" />
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
import 'vue-skeletor/dist/vue-skeletor.css';
import { Skeletor } from 'vue-skeletor';
import useVuelidate from '@vuelidate/core'
import { required, email, minLength, maxLength, sameAs } from '@vuelidate/validators'
export default {
    name: 'AdminLogin',
    components: {
        Skeletor
    },
    setup() {
        return { v$: useVuelidate() }
    },
    data() {
        return {
            loading: true,
            fname: '',
            lname: '',
            username: '',
            email: '',
            password: '',
            confirm_password: '',
            gender: '',
        }
    },
    validations() {
        return {
            fname: { required },
            lname: { required },
            username: { required, minLength: minLength(6), maxLength: maxLength(12) },
            email: { required, email },
            password: { required, minLength: minLength(6) },
            confirm_password: {
                sameAsPassword: sameAs(this.password)
            } 

        }
    },
    methods: {
        async onSubmit() {
            let formCheck = await this.v$.$validate()
            if (!formCheck) return
        }
    },
    mounted() {

        setTimeout(console.log('add loading for 5 sec '), 5000)

    }
}
</script>
<style>
.main-parent {
    min-height: 100vh;
}

.admin-login-form {
    width: 45%;
}

.admin-login-form .input-group .input-group-text {
    background-color: var(--ln-black);
}

.admin-login-form .input-group input {
    background-color: var(--ln-black);
    color: var(--ln-white);
}

.admin-login-form .input-group input:focus {
    border-color: var(--ln-gray);
    box-shadow: none;
}

.admin-login-form .input-group input::placeholder {
    color: var(--ln-gray);
}

@media all and (min-width: 320px) and (max-width: 767px) {
    .admin-login-form {
        width: 100%;
    }
}
</style>