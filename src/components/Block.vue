<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Klikni!
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },

    /** LIFECYCLE HOOKS */
    mounted() {
        setTimeout(() => {
            // console.log ('Component mounted')
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            console.log(this.reactionTime)
            this.$emit('end', this.reactionTime) /** custom event */
        }
    }
    // updated(){
    //     console.log ('Component updated')
    // },
    // unmounted(){
    //     console.log ('Component unmounted')
    // }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>
