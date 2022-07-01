<template>
    <div :id="id" class="offer">
        <p class="offer-info"> {{info}} </p>
        <span class="material-icons offer-remove" @click="remove">
            remove_circle
        </span>
    </div>
</template>
<script>
    export default {
        data() {
            return {
               
            }
        },
        methods: {
            remove() {
                //bedo y2ol la bayo eno 5od this is my id(row) and , u (parent) make a request and delete
                this.$emit('remove',this.id)

            }
        },
        props: ['id', 'info'],


    }
</script>
<style>
    .offer {
        display: flex;
        max-width: 90%;
        justify-content: space-between;
        align-items: center;
        margin: 1em auto;

    }

    .offer-info {

        width: 90%;
        border: 1px solid #777;
        border-radius: 1em;
        font-size: 2em;
        padding: 1em;
        text-align: center;
        height: fit-content;
        color: rgb(216, 216, 216);
        background-color: rgb(38, 38, 38);
        margin-right: 1em;
        overflow-wrap: break-word;

    }

    .offer-remove {

        font-size: 3em;
        cursor: pointer;

    }
</style>