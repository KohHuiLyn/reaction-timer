<template>
  <div class="block" v-if="showBlock" @click="computeRxn">
      Click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
            timeShown: null
        }
    },
    mounted(){
        console.log("IM HERE! ITS ME!!!")
        setTimeout(() => {
            this.showBlock = true;
            // this.startTimer()
        }, this.delay)
    },
    updated(){
        console.log("updated")
        this.timeShown = Date.now()
    },
    // unmounted(){
    //     console.log("Bye....")
    // },
    methods: {
        computeRxn(){
            console.log("onclick")
            this.reactionTime =  (Date.now() - this.timeShown)/1000
            console.log("timeshown" + this.timeShown + "now "+ Math.floor(Date.now() / 1000) + " rxn "+this.reactionTime)
            // this.reactionTime= "hi"
            //Function to end the timer and send back to App.vue
            this.$emit('end', this.reactionTime)
        }
        // startTimer(){
        //     this.timer = setInterval( ()=> {
        //         //every 10ms, increase reaction time by 10ms
        //         this.reactionTime += 10;
        //     }, 10)
        // },
        // stopTimer(){
        //     clearInterval(this.timer)
        //     this.$emit('end', this.reactionTime)
        // }
    }
}
</script>

<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background: rgb(69, 180, 97);
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>