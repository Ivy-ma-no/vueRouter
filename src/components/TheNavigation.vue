<template>
    <div class="wrapper">
        <nav id="nav">
            <RouterLink id="logo" to="/">
                My sweetest sweets
            </RouterLink>
            <RouterLink v-for="destination in destinations" :key="destination.id"
                :to="{ name: 'destination.show', params: { id: destination.id, slug: destination.slug } }">
                {{ destination.name }}
            </RouterLink>
            <RouterLink :to="{ name: 'protected' }">My account
            </RouterLink>
        </nav>
    </div>
</template>

<script>
import sourceData from '@/data.json'
export default {
    data() {
        return {
            destinations: sourceData.destinations
        }
    }
}
</script>