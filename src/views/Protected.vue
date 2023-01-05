<template>
    <div>Protected
        <p>Greetings, {{ username }}</p>
        <button @click="logout">Logout</button>
        <RouterLink to="/invoices"><button>Invoices</button></RouterLink>
    </div>
</template>

<script>
export default {
    data() {
        return {
            username: window.user
        }
    },
    methods:{
    logout(){
        window.user = null
        //redirect to homepage
        this.$router.push({name:'home'})
    }}
}
</script>