<template>
    <input type="text" v-model="title" id="title" />
    <button @click="mysubmit">test</button>
    <div id="content"></div>
</template>

<script>

import { hasGrantedAnyScopes } from "vue3-google-signin";

export default {

    props: {
        token: String,
    },


    data() {
        return {
            title: '',
        }
    },

    methods: {

        mysubmit() {
            var myHeaders = new Headers();
            myHeaders.append("Authorization", "Bearer "+this.token);

            var requestOptions = {
                method: 'GET',
                headers: myHeaders,
                redirect: 'follow'
            };

            fetch("https://slides.googleapis.com/v1/presentations/1EAYk18WDjIG-zp_0vLm3CsfQh_i8eXc67Jo2O9C6Vuc", requestOptions)
                .then(response => response.text())
                .then(result => console.log(result))
                .catch(error => console.log('error', error));
        }


        // mysubmit() {
        //     let myinput = this.title
        //     gapi.load('client', this.start);
        // },

        // start() {
        //     // 2. Initialize the JavaScript client library.
        //     gapi.client.init({
        //         // clientId and scope are optional if auth is not required.
        //         'clientId': '701546085277-t9fi4hfsn19emb1kddj5rfpk9sldnf4k.apps.googleusercontent.com',
        //         'scope': 'https://www.googleapis.com/auth/presentations',
        //     }).then(function () {
        //         // 3. Initialize and make the API request.
        //         return gapi.client.request({
        //             'path': 'https://slides.googleapis.com/v1/presentations/1EAYk18WDjIG-zp_0vLm3CsfQh_i8eXc67Jo2O9C6Vuc',
        //         })
        //     }).then(function (response) {
        //         console.log(response.result);
        //     }, function (reason) {
        //         // console.log('Error: ' + reason.result.error.message);
        //         console.log(JSON.stringify(reason))
        //     }); 
        // }



    },
}

</script>




<style>

</style>