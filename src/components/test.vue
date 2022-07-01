<template>
    <button @click="sendvoice">emit now</button>
</template>
<script>
    export default{
        methods:{
            sendvoice(){
                alert('emit started')
                this.$emit('yamama','123')
                alert('emit ended')

            }
        }
    }
</script>