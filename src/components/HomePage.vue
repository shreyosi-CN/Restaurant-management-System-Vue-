<template>
<HeaderPage />
<h1>Hello {{name}} Welcome to home page</h1>
<table class="table">
    <thead>
        <tr>
            <th>SL No</th>
            <th>Name</th>
            <th>Address</th>
            <th>Phone</th>
            <th>Actions</th>
        </tr>
    </thead>
    <tbody>
        <tr v-for="items in restaurant" :key="items.id">
            <td>
                {{ items.id }}
            </td>
            <td>
                {{ items.name }}
            </td>
            <td>
                {{ items.address }}
            </td>
            <td>
                {{ items.contact }}
            </td>
            <td>
                <router-link :to="'/update/'+items.id">Update</router-link>
                <button v-on:click="deleteRestro(items.id)">Delete</button>
            </td>
        </tr>
    </tbody>
</table>
</template>

<script>
import HeaderPage from './HeaderPage.vue'
import axios from 'axios'
export default {
    name: "HomePage",
    data() {
        return {
            name: '',
            restaurant: []
        }
    },
    methods: {
        async deleteRestro(id) {
            let result = await axios.delete("http://localhost:3000/restaurant/" + id);
            if (result.status == 200) {
                this.loadRestro()

            }
            console.warn(result);

        },
        async loadRestro() {
            let user = localStorage.getItem("user-info");
            this.name = JSON.parse(user).name
            if (!user) {
                this.$router.push({
                    name: 'SignUp'
                })

            }

            let result = await axios.get("http://localhost:3000/restaurant");
            this.restaurant = result.data;
        }
    },
    components: {
        HeaderPage
    },
    mounted() {
        this.loadRestro()
    }

};
</script>

<style>
.table td {
    width: 160px;
    border: 1px solid;
    padding: 5px;
    height: 40px;
}

.table th {
    font-size: 20px;
    color: blue;
}
</style>
