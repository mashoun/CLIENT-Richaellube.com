<template>
    <div class="toolbar">
        <label class="title">Richaellube.com</label>
        <div class="toolbar-icons">

            <span class="material-icons password-icon" @click="getpassword()">
                password
            </span>
            <span class="material-icons sync-icon" @click="refresh_data">
                cached
            </span>

        </div>
    </div>

    <div class="offer-bar">
        <p id="new-offer" class="offer-input" contenteditable>write new offer</p>
        <span class="material-icons add-offer" @click="add">
            add_circle_outline
        </span>
    </div>

    <!-- Spinner -->
    <progress v-if="spinner"></progress>
    <!-- List of offers -->
    <div class="offers-container">
        <offer v-for="o in offers" :key="o" :id="o.id" :info="o.data" @remove="offer_remove">

        </offer>
    </div>


</template>
<script>
    import offer from '@/components/offer.vue'
    export default {
        data() {
            return {

                api: "https://script.google.com/macros/s/AKfycbxD05VBPB7dccLaERZjmlPrf08Qv12ntqQSVKWs11VRWDykxxP8dd_u4RtsMCK9ZxSy2w/exec",
                spinner: false,
                offers: [],
                ssap: false
            }

        },
        components: {
            offer
        },
        mounted() {

            let api = this.api;
            let queryGET = "?getdata=1"
            api += queryGET;

            this.spinner = true;
            fetch(api).then(res => res.json())
                .then(result => {
                    //console.log(result)
                    this.offers = result;
                    this.spinner = false;
                })

        },
        methods: {
            offer_remove(row_id) {
                //lama y7ot el pass mn el eben ( offer minus )
                //alert(row_id)

                let api = this.api;
                let queryGET = `?pop=1&p=${this.ssap}&row=${row_id + 2}`;
                api += queryGET;
                //console.log(queryGET);
                this.spinner = true;
                fetch(api).then(res => res.json())
                    .then(result => {
                        if (result == '200') alert("مشي الحال");
                        else alert("للاسف حاول مرة تانية");
                        this.spinner = false;
                    })

                this.refresh_data();
            },
            getpassword() {
                this.ssap = prompt("3atene el password")
                return this.ssap;

            },
            refresh_data() {
                let api = this.api;
                let queryGET = "?getdata=1"
                api += queryGET;

                this.spinner = true;
                fetch(api).then(res => res.json())
                    .then(result => {
                        //console.log(result)
                        this.offers = result;
                        this.spinner = false;
                    })
            },
            add() {
                //var the_new_offer = document.getElementById('new-offer').innerText;
                //call the api and send
                if (!this.ssap) {
                    this.ssap = prompt('ENTER PASSWORD');
                }
                //console.log(this.ssap)

                var thenewoffer = document.getElementById('new-offer').innerText;
                console.log(thenewoffer);

                let api = this.api;
                let queryGET = `?add=1&p=${this.ssap}&newdata=${thenewoffer}`
                api += queryGET;

                this.spinner = true;
                fetch(api).then(res => res.json())
                    .then(result => {
                        if (result == '200') alert("مشي الحال");
                        else alert("للاسف حاول مرة تانية");
                        this.spinner = false;
                    })

                document.getElementById('new-offer').innerText = "";
                this.refresh_data();




            }
        }
    }
</script>
<style>
    @import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@300&display=swap');
    *{ font-family: 'Comfortaa', cursive; }
    .toolbar {
        display: flex;
        background-color: #4885ed;
        justify-content: space-between;
        align-items: center;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
        width: 100vw;
        
        
        
    }

    .title {
        font-size: 2em;
        color: antiquewhite;
        margin: 1em;
    }

    .toolbar-icons {
        display: flex;
        justify-content: flex-end;
        width: 70%;
    }

    .password-icon {
        font-size: 2em;
        color: antiquewhite;
        margin: 1em;
        cursor: pointer;
    }

    .sync-icon {
        font-size: 2em;
        color: antiquewhite;
        margin: 1em;
        cursor: pointer;
    }

    fieldset {
        border-radius: 20px;
        border-style: none;

    }

    .offer-bar {
        display: flex;
        max-width: 90%;
        justify-content: space-between;
        align-items: center;
        margin: 1em auto;
    }

    .offer-input {
        width: 90%;
        border: 1px solid #777;
        border-radius: 1em;
        font-size: 2em;
        padding: 1em;
        text-align: center;
        height: fit-content;
        color: #777;
        margin-right: 1em;
        overflow-wrap: break-word;


    }

    .add-offer {
        font-size: 3em;
        cursor: pointer;

    }

    @media (max-width:500px){
        *{ font-size: 11px;}

    }
    @media (max-width:350px){
        *{ font-size: 10px;}

    }
    @media (max-width:310px){
        *{ font-size: 9px;}

    }
    @media (max-width:280px){
        *{ font-size: 8px;}

    }
    @media (max-width:250px){
        *{ font-size: 7px;}

    }
</style>