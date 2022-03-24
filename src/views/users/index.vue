<template>
    <div class="user-list-container">
        {{userList}}
    </div>
</template>

<script>
import { getUserList } from '@/api/user'
import { title } from '@/settings'
export default {
    data() {
        return {
            userList: []
        }
    },
    created() {
        this.fetchData()
    },
    methods: {
        fetchData() {
            getUserList().then(response => {
                this.userList = response.results
            })
        }
    }
}
</script>

<style scoped>

</style>
