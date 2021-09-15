<template>
    <v-btn @click="deleteAllPosts()" icon color="black" fixed right>
        <v-icon>mdi-refresh</v-icon>
      </v-btn>
</template>

<script>
export default {
    setup() {
        
    },
    methods: {
        deleteAllPosts() {
            
            this.$emit("delete-all")
        }
    }
}
</script>