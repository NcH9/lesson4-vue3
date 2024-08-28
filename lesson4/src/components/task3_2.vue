<!-- Виведення вкладених об’єктів:
Реалізуйте компонент, що виводить список об'єктів, де кожен об'єкт має вкладений список. 
Використовуйте вкладені v-for для виведення елементів вкладеного списку. -->

<template>
    <div class="task">
        <ul>
            <li v-for="(list, index) in listOfLists">
                <p>list #{{ index+1 }}</p>
                <ul>
                    <li v-for="(item, index) in list">
                        {{ item.text }}
                    </li>
                </ul>
            </li>
        </ul>
        <button @click="fillLists">fill lists</button>
    </div>
</template>
<script type="module">
    export default{
        name: 'task3_2',
        data(){
            return {
                listOfItems: [],
                listOfLists: [],
            }
        },
        methods: {
            getRandomNumber(min, max){
                return Math.floor(Math.random() * (max - min + 1) + min) ;
            },
            fillItems(amount){
                this.listOfItems = [];
                for (let i = 0; i < amount; i++){
                    const newItem = {
                        text: `this is item ${i+1}`
                    }
                    this.listOfItems.push(newItem);
                }
                this.listOfLists.push(this.listOfItems);
            },
            fillLists(){
                this.listOfItems = [];
                this.listOfLists = [];
                const lengthOfListOfLists = this.getRandomNumber(1,5);
                for (let i = 0; i < lengthOfListOfLists; i++){
                    const lengthOfListOfItems = this.getRandomNumber(1, 5);
                    this.fillItems(lengthOfListOfItems);
                } 
            }
        }
    }
</script>