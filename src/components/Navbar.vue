<script setup lang="ts">
    //imports
    import {ref, watch} from "vue"
    
    //props
    const props = defineProps(["showNumbers"])
  

    //styles
    const spanStylingSelected = "border-b-[4px] border-green-400  border-dotted"

    //functions


</script>

<template>
    <div class="flex justify-center gap-10">
        <span 
            :class="`${showNumbers ? spanStylingSelected : ''}`"
            @click="$emit('changeView', true)"
        >
            Numbers
        </span>

        <span 
            :class="`${!showNumbers ? spanStylingSelected : ''}`"
            @click="$emit('changeView', false)"
        >
            Contacts
        </span>

    </div>
</template>

<style>

    span {
        cursor: pointer;
        user-select: none;
    }
</style>