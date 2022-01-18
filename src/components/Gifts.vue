<template>
    <div>
        <h1>
            Gifts
        </h1>
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
                gifts : []
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
        }
    }
</script>