<template>
<HeaderPage />
<h1>Hello, Welcome to Update Resturant page</h1>
<form class="form">
    <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name" />
    <input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address" />
    <input type="text" name="contact" placeholder="Enter contact" v-model="restaurant.contact" />
    <button type="button" v-on:click="update">Update Restaurant</button>

</form>
</template>

<script>
import axios from 'axios';
import HeaderPage from './HeaderPage.vue'
export default {
    name: "UpdateResturant",
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
        async update() {
            let result = await axios.put("http://localhost:3000/restaurant/" + this.$route.params.id, {
                name: this.restaurant.name,
                address: this.restaurant.address,
                contact: this.restaurant.contact
            });
            if (result.status == 200) {
                this.$router.push({
                    name: 'HomePage'
                })

            }
            this.restaurant = result.data;

        }
    },

    components: {
        HeaderPage
    },
    async mounted() {
        let user = localStorage.getItem("user-info");
        if (!user) {
            this.$router.push({
                name: 'SignUp'
            })

        }

        let result = await axios.get("http://localhost:3000/restaurant/" + this.$route.params.id);
        console.warn(result);
        this.restaurant = result.data;

        console.warn(this.$route.params.id);
    }

};
</script>
