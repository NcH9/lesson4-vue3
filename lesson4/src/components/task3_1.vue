<!-- Динамічне створення таблиці:
За допомогою v-for, створіть таблицю, де кількість рядків і стовпців задається динамічно через інпут або інший елемент керування. -->

<template>
    <div class="task">
        <input type="number" v-model="numberOfElems">
        <button @click="createElements">create {{ numberOfElems }} elements</button>
        <ul>
            <li v-for="(item, index) in listItems" :key="index">
                {{ item.text }}
            </li>
        </ul>
    </div>
</template>
<script type="module">
    export default{
        name: 'task3_1',
        data(){
            return {
                numberOfElems: 0,
                listItems: [],
            }
        },
        methods: {
            generateItems(amount){
                for (let i = 0; i < amount; i++){
                    const newItem = {
                        text: `this is element #${i+1}`,
                    }
                    this.listItems.push(newItem)
                }
            },
            createElements(){
                this.listItems = [];
                if (this.numberOfElems > 0){
                    this.generateItems(this.numberOfElems);
                } else {
                    alert('number of elements must be higher than 0');
                }
            }
        },
    }
</script>