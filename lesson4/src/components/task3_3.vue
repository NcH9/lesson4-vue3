<!-- Пагінація списку:
Виведіть довгий список елементів з пагінацією, використовуючи v-for, і динамічно змінюйте відображені елементи при кліку на кнопки пагінації.
Виведіть список елементів, використовуючи v-for, і додайте умову v-if для фільтрації елементів. -->

<template>
    <div class="task">
        <input type="number" placeholder="lower number" v-model="lowerNum">
        <input type="number" placeholder="upper number" v-model="upperNum">
        <ul>
            <div v-for="(item, index) in listToShow" :key="index">
                <li v-if="index >= lowerNum-1 && index <= upperNum-1">
                    {{ item.text }}
                </li>
            </div>
        </ul>
        <button @click="generateList">generate list</button>
    </div>
</template>
<script type="module">
    export default{
        name: 'task3_3',
        data(){
            return {
                listOfItems: [],
                listToShow: [],
                lowerNum: 0,
                upperNum: 100,
            }
        },
        methods: {
            getRandomNumber(min, max){
                return Math.floor(Math.random() * (max - min + 1) + min) ;
            },
            generateList(){
                this.listOfItems = [];
                for (let i = 0; i < this.getRandomNumber(11, 40); i++) {
                    const newItem = {
                        text: `Item #${i+1}`
                    };
                    this.listOfItems.push(newItem);
                }
                this.listToShow = this.listOfItems;
            },
        }
    }
</script>