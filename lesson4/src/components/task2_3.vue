<!-- Створіть переключатель тем, який динамічно змінює стилі всього додатку між темною та світлою темами. -->

<template>
    <div class="task">
        <button @click="changeTheme">Change Theme</button>
    </div>
</template>
<script type="module">
    export default{
        name: 'task2_3',
        data(){
            return {
                
            }
        },
        methods: {
            changeTheme(){
                const body = document.body;
                if (body.classList.contains('light-theme')){
                    body.classList.remove('light-theme');
                } else {
                    body.classList.add('light-theme');
                }
            }
        }
    }
</script>
<style scoped>
</style>