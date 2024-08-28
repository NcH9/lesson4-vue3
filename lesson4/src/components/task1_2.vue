<template>
    <div class="task">
        <form @submit.prevent="handleSubmit">
            <input type="text" placeholder="login" :value="form.login" @input="form.login = $event.target.value"/>
            <span v-if="error.login" color="red">{{ error.login }}</span>

            <input type="password" placeholder="password" :value="form.password" @input="form.password = $event.target.value"/>
            <span v-if="error.password" color="red">{{ error.password }}</span>

            <span>{{ form.isSubmited }}</span>
        </form>
        <button @click="submit">submit form</button>
    </div>
    
</template>

<script type="module">
    export default {
        name: 'task1_2',
        data() {
            return {
                form: {
                    login: '',
                    password: '',
                    isSubmited: '',
                },
                error: {},
            }
        },
        methods: {
            submit () {
                this.form.isSubmited = '';
                this.error = this.validateForm();
                if (Object.keys(this.error).length == 0){
                    this.submitFinale();
                }
            },
            validateForm() {
                let errors = {};
                if (this.form.login.length < 3){
                    errors.login = 'login must be 3 or more symbols long';
                } else if (this.form.login.length > 15) {
                    errors.login = 'login must be shorter than 15 symobols';
                }
                if (this.form.password.length < 3){
                    errors.password = 'password must be 3 or more symbols long';
                }
                return errors;
            },
            submitFinale(){
                this.form.isSubmited = 'Form successfully submited!';
                this.form.login = '';
                this.form.password = '';
            },
        },
    }
    
</script>