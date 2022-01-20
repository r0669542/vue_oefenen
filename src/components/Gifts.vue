<template>
    <div>
        <h1>
            Gifts
        </h1>
        <div>
            <input v-model="kado" placeholder="kado">
            <input v-model="receiver" placeholder="receiver">
            <button @click="addGift(kado,receiver)">
                    Add gift
            </button>
        </div>
        <div v-for="gift in gifts" :key="gift.id">
            {{ gift.name}} - {{ gift.receiver }}
        </div>
    </div>
</template>

<script>
    export default {
        name: "Homepage",
        data() {
            return {
                gifts : [],
                kado : "",
                receiver : ""
            }
        },
        mounted() {
            this.fetchGifts();
        },
        methods: {
            fetchGifts() {
                const url = "http://localhost:41391/Gift";
                fetch(url)
                    .then((response) => {
                        return response.json();
                    })
                    .then((gifts) => {
                        
                        this.gifts = gifts;
                        console.log(gifts);
                    }
                );
            },
            addGift(kado,receiver){
                const url = "http://localhost:41391/Gift";
                this.kado = kado;
                this.receiver = receiver;

                fetch(url, {
                    method: "POST",
                    headers: {
                        'Accept': 'application/json, text/plain',
                        'Content-Type': 'application/json;charset=UTF-8'
                    },
                    body: JSON.stringify({
                        name : this.kado,
                        receiver : this.receiver
                    })
                }).then((response) => {
                    return response.json();
                }).then((result) => {
                    console.log(result);
                })
            }
        }
    }
</script>