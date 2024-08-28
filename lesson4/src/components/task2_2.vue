<!-- Реалізуйте динамічне змінення стилів елемента (наприклад, зміна позиції, коліру, розміру) 
за допомогою CSS Transitions або Animations при натисканні кнопки. -->

<template>
    <div class="task">
        <div class="thisElem" :class="{active:isActive}">Hello~!</div>
        <button @click="changeStyle">Click</button>
    </div>
</template>
<script type="module">
    export default{
        name: 'task2_2',
        data(){
            return {
                isActive: false,
            }
        },
        methods: {
            changeStyle(){
                this.isActive = !this.isActive;
            }
        }
    }
</script>
<style scoped>
.thisElem {
    display: flex;
    justify-content: center;
    border-radius: 15px;
    width: 150px;
    height: 40px;
    background-color: rgba(19, 45, 70, 0.5);
    padding: 10px;
}
.thisElem.active {
    width: 300px;
    height: 60px;
    background-color: rgb(30, 73, 112, 0.5);
    justify-content: flex-end;
}
</style>