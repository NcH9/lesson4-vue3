<!-- Створіть динамічний список елементів, де кожен елемент має випадковий колір фону та розмір шрифту,
згенеровані методом при створенні компоненту. -->

<template>
    <div class="task">
        <ul>
            <li v-for="(item, index) in listItems" :key="index" :style="item.style">
                {{ item.text }}
            </li>
        </ul>
    </div>
</template>
<script type="module">
    export default{
        name: 'task2_1',
        data(){
            return {
                listItems: [],
            }
        },
        methods: {
            getRandomColor(){
                const color = this.getRandomNumber(1, 3);
                switch (color)
                    {
                        case 1:
                            return 'rgb(255, 0, 0)';
                        case 2:
                            return 'rgb(0, 255, 0)';
                        case 3:
                            return 'rgb(0, 0, 255)';
                    }
            },
            getRandomNumber(min, max){
                return Math.floor(Math.random() * (max - min + 1) + min) ;
            },
            generateItems(amount){
                for (let i = 0; i < amount; i++){
                    const newItem = {
                        text: `this is element #${i+1}`,
                        style: {
                            color: this.getRandomColor(),
                            fontSize: this.getRandomNumber(14, 26)+'px',
                        }
                    }
                    this.listItems.push(newItem)
                }
            }
        },
        created() {
            this.generateItems(this.getRandomNumber(3, 5))
        }
    }
</script>
<style scoped>
ul {
    border-radius: 15px;
}

li {
    padding: 10px;
    margin: 5px;
    color: white;
    border-radius: 15px;
}
</style>