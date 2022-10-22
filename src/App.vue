<script setup>
  //library imports
  import { Icon } from '@iconify/vue';

  //imports
  import {ref, reactive} from "vue"

  //components
  import View from "./components/View.vue"
  import Contacts from "./components/Views/Contacts.vue"
  import Numbers from "./components/Views/Numbers.vue"
  import Navbar from "./components/Navbar.vue"

  //variables
  const showNumbers = ref(true)
  const contacts = reactive([
    {
      name: "Jhon Doe",
      number: "983013992"
    }
  ]) 

  //functions

  //-emits
  const changeView = (value) => {
      showNumbers.value = value
  }
</script>

<template>
  <main class="relative flex flex-col m-auto justify-center items-center h-[85vh] w-[35vw] bg-white rounded-md">
    <h1 class="flex text-white justify-between absolute top-0 bg-neutral-900 w-full rounded-b-sm p-2">
      <span class="mx-2 flex items-center gap-2">
        Connected
        <Icon icon="icomoon-free:connection" />
      </span>
      <span>
        10:14
      </span>
      <span class="mx-2 flex items-center gap-2">
        89%
        <Icon icon="ic:baseline-battery-80"/>
      </span>
    </h1>
    
    <View @newContact="(n) => console.log('newContact', n)">
      <Numbers v-if="showNumbers" :contacts="contacts"/>
      <Contacts v-if="!showNumbers" :contacts="contacts"/>
    </View>

    <Navbar 
      class="absolute bottom-0 p-4"
      @changeView="changeView"
      :showNumbers="showNumbers"
    />
  </main>

</template>

<style scoped>
  
</style>
