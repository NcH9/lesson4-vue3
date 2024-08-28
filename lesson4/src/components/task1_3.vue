<template>
    <div class="task">
        <div>{{ number }}</div>
        <button @click="handleClick">Click</button>
    </div>
</template>

<script type="module">
    export default {
        name: 'task1_3',
        data(){
            return {
                number: 0,
            }
        },
        methods: {
            increment(){
                this.number++;
            },
            decrement(){
                this.number--;
            },
        },
        computed: {
            handleClick(){
                if (this.number > 5){
                    return this.decrement;
                } else if (this.number >= 0 && this.number <=5){
                    return this.increment;
                }
            }
        },
    }
</script>