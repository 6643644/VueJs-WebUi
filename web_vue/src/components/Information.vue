<template>
    <div>
        <h1>Welcome!</h1>
        <div>
            <b-button @click="getInfo()">Get your information</b-button>
            <h2 v-if="username !== ''">Your username is: {{ username }}</h2>
            <h2 v-if="password !== ''">Your email is: {{ password }}</h2>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data () {
        return {
            username: '',
            password: ''
        };
    },
    methods: {
        getInfo () {
            axios.get('http://localhost:8090/testCha/Show')
            .then((response) => {
                this.username = response.data['username'];
                this.password = response.data['password'];
                console.log(response);
            }).catch((error) => {
                console.log(error);
            });
        }
    }
}
</script>