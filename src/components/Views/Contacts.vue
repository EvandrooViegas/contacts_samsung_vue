<script setup>
    const props = defineProps(["contacts"])
    const {contacts} = props

    const newContact = {
        number: "",
        name: ""
    }

    const openPrompt = () => {
        newContact.number = prompt("New Number")
        newContact.name = prompt("New Name")

        props.contacts.push(newContact)
    }
</script>

<template>
    <div class="flex flex-col justify-center items-center gap-4 px-10 py-5">
   
        <div class="w-full flex justify-between">
            <h3 class="font-semibold">New Contact</h3>
            <button 
                class="bg-green-600 w-8 h-8 rounded-full text-white"
                @click="openPrompt()"
            >
                +
            </button>
        </div>
        <div class="w-full flex-col gap-10 justify-center items-center"> 
            <div 
            v-for="contact in contacts" 
            :key="contact.number"
            class=" flex m-auto justify-between bg-neutral-200 p-4 rounded-md mt-3">
                <span class="font-semibold">{{ contact.name }}</span>
                <span class="hover:text-green-400">{{ contact.number }}</span>
            </div>
        </div>
    </div>
</template>