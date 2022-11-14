<template>
    <h2>{{userName}}</h2>
    <h3>{{age}}</h3>
</template>

<script>
import { computed, inject } from 'vue';

export default {
    props:['firstName', 'secondName'],
    setup(props, context){
        let userName = computed(function() {
            return props.firstName + ' ' + props.secondName
        })
        console.log( context)
        const age = inject('userAge')
        return {
            userName,
            age
        }
    }
    // computed: {
    //     userName() {
    //         return this.firstName + ' ' + this.secondName
    //     }
    // }
}
</script>