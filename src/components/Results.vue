<template>
    <p>Reaction time - {{score}} ms</p>
    <p class="rank">{{rank}}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return {
            rank: null
        }
    },
    mounted(){
        if (this.score < 250) {
            this.rank = 'Woooow!'
        } else if (this.score < 400) {
            this.rank = 'Rychlý'
        } else {
            this.rank = 'Nic moc'
        }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4 em;
        color: #0faf87;
        font-weight: bold;
    }
</style>
