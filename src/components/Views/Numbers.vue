<script setup>
    //imports
    //library imports
    import { Icon } from '@iconify/vue';
    import {computed, reactive, ref, watch} from "vue"

    //variables
    const numberStr = ref("")
    const props = defineProps(["contacts"])
    const filteredNumbers = ref(props.contacts)
   
    //functions
    const incrementValue = (value) => {
        if(value == "remove") {
            let newValue = ""
            for (let i = 0; i < numberStr.value.length; i++) {
                if(i == numberStr.value.length - 1) {} 
                else newValue += numberStr.value[i]  
            }
            numberStr.value = newValue
        } else {
            numberStr.value += value 
        }

    }

    //computed
    watch(numberStr, () => {
        props.contacts.filter(c => c.number.includes(numberStr.value))
    
        if(numberStr) {
            filteredNumbers.value = props.contacts.filter(c => c.number.includes(numberStr.value))
        } else {
            filteredNumbers.value = props.contacts
        }
    })
</script>

<template>
    <div class="flex flex-col justify-evenly h-full">
        <div>
            <div class="w-full flex-col gap-10 justify-center items-center p-4 overflow-scroll overflow-x-hidden h-60"> 
                <div 
                v-for="contact in filteredNumbers" 
                :key="contact.number"
                class=" flex m-auto justify-between bg-neutral-200 p-4 rounded-md mt-3">
                    <span class="font-semibold">{{ contact.name }}</span>
                    <span class="hover:text-green-400">{{ contact.number }}</span>
                </div>
            </div>
        </div>
        <div class="flex flex-col gap-2 items-center">
            
            <div class="text-2xl m-auto">
                <input v-model="numberStr" type="number" class="text-center outline-none border-none"/>
            </div>
            <div class="flex flex-col gap-4 items-center  w-[40%]">
                <div class="grid grid-cols-3 gap-4 m-auto w-full" id="grid">
                <button @click="incrementValue('1')">1</button>
                <button @click="incrementValue('2')">2</button>
                <button @click="incrementValue('3')">3</button>
                <button @click="incrementValue('4')">4</button>
                <button @click="incrementValue('5')">5</button>
                <button @click="incrementValue('6')">6</button>
                <button @click="incrementValue('7')">7</button>
                <button @click="incrementValue('8')">8</button>
                <button @click="incrementValue('9')">9</button>
                <button @click="incrementValue('')">*</button>
                <button @click="incrementValue('0')">0</button>
                <button @click="incrementValue('')">#</button>

            </div>
            <div class="flex gap-10 justify-center w-full">
                <Icon icon="cil:delete"  @click="incrementValue('remove')"/>
                <Icon icon="fluent:call-24-regular" @click="incrementValue('')"/>
            </div>
            </div>
        </div>
    </div>
</template>

<style>
    #grid > button {
        font-size: 20px;
        padding: 10px;
    }

    #grid > button:hover {
        background: #DDD;
        border-radius: 50%;
    }
</style>