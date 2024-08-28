<template>
    <div class="task">
        <div>
            {{ currentTimeArray }}
        </div>
        <button @click="saveCurrentTime">save time</button>
    </div>
</template>

<script type="module">
    export default {
        name: 'task1_1',
        data() {
            return {
                currentTimeArray: [],
            }
        },
        methods: {
            saveCurrentTime() {
                this.currentTimeArray.push(this.getCurrentTime())
            },
            getCurrentTime(){
                const now = new Date();
                return now.toLocaleTimeString();
            }
        },
    }
    
</script>