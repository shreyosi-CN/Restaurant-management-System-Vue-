<template>
<HeaderPage />
<h1>Hello, Welcome to Add Resturant page</h1>
<form class="form">
    <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name" />
    <input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address" />
    <input type="text" name="contact" placeholder="Enter contact" v-model="restaurant.contact" />
    <button type="button" v-on:click="add">Add Restaurant</button>

</form>
</template>

<script>
import axios from 'axios';
import HeaderPage from './HeaderPage.vue'
export default {
    name: "AddResturant",
    data() {
        return {
            restaurant: {
                name: '',
                address: '',
                contact: ''
            }

        }
    },
    methods: {
        async add() {
            console.warn(this.restaurant.name);
            let result = await axios.post("http://localhost:3000/restaurant", {
                name: this.restaurant.name,
                address: this.restaurant.address,
                contact: this.restaurant.contact
            });
            if(result.status == 201)
            {
              this.$router.push({name:'HomePage'})

            }
        }
    },
    components: {
        HeaderPage
    },
    mounted() {
        let user = localStorage.getItem("user-info");
        if (!user) {
            this.$router.push({
                name: 'SignUp'
            })

        }

    }

};
</script>
