<script setup>
import {ref, reactive} from 'vue'
import Resume from './Resume.vue';

const optionsArray = reactive([
    {id: 0, title: "Заголовок", text: "", value:"title"},
    {id: 1, title: "Подзаголовок", text: "", value:"subtitle"},
    {id: 2, title: "Аватар", text: "", value:"avatar"},
    {id: 3, title: "Текст", text: "", value:"text"}
])

let idx = 0

const select = ref("")
const textValue = ref("")

select._value = 0      //По умолчанию Заголовок выбран


function getOptionsKey(event) {
    return idx = event.target.value
}


function selectOption(selectedIndex) {
    if(selectedIndex == optionsArray[0].id)
        optionsArray[0].text = textValue.value
    
    if(selectedIndex == optionsArray[1].id)
        optionsArray[1].text = textValue.value
    
    if(selectedIndex == optionsArray[2].id)
        optionsArray[2].text = textValue.value
    
    if(selectedIndex == optionsArray[3].id)
        optionsArray[3].text = textValue.value

    textValue.value = ""
    select._value = 0
}

</script>

<template>
     <form class="card card-w30" 
        @submit.prevent="">
        <div class="form-control">
            <label for="type">Тип блока</label>
            <select id="type" v-model="select" @change="getOptionsKey($event)">
                <option v-for="option in optionsArray" :key="option.id" :value="option.id">{{ option.title }}</option>
            </select>
        </div>

        <div class="form-control">
            <label for="value">Значение</label>
            <textarea id="value" rows="3" v-model="textValue"></textarea>
        </div>

        <button type="submit" @click="selectOption(idx)" class="btn primary">Добавить</button>
     
    </form>    
    
    <Resume
        :title="optionsArray[0].text"
        :subtitle="optionsArray[1].text"
        :avatar="optionsArray[2].text"
        :text="optionsArray[3].text">
    </Resume>
</template>