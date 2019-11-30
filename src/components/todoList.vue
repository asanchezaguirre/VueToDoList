<template>
    <ul class="list-group">
      <li 
        v-for="(item, index) in list" 
        v-bind:key= "index"
        class="list-group-item">
        {{ item.label }} - {{ item.done ? "completed" : "pending"}}
        <button 
          v-on:click="toggle(item)"
          class= "btn btn-sm btn-primary float-right">toggle
        </button>
        </li>
    </ul>
</template>

<script>
export default {
    props:{
        list:{
            type: Array,
            default: () => []
        }
    },
    methods:{
        toggle(item){
            this.$emit('toggle', item);
        }

    }
}
</script>