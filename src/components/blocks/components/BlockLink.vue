<template>
    <div ref="editorLink" class="w-1/4 flex flex-col">
        <!-- <div class="p-1 bg-gray-200 w-full" @click="$emit('close')">Link</div> -->
        <div class="flex items-center p-1">
            <m-icon icon="link"/><input v-if="$store.state.editor.current" class="ml-2 p-1 rounded w-56 text-lg" v-model="$store.state.editor.current.link"/>
            <m-icon icon="keyboard_return" class="bg-indigo-500 text-white p-1 rounded ml-1" @click="$emit('input',link)"/>
            <m-icon icon="link_off" class="shadow p-1 rounded ml-1" @click="$emit('input','')"/>
        </div>
        <div class="flex items-center p-1" title="anchor">
            <m-icon icon="anchor"/>
            <input v-if="$store.state.editor.current" class="ml-2 p-1 rounded w-56 text-lg" v-model="$store.state.editor.current.anchor"/>
            <m-icon icon="keyboard_return" class="bg-indigo-500 text-white p-1 rounded ml-1" @click="$emit('input',link)"/>
            <m-icon icon="link_off" class="shadow p-1 rounded ml-1" @click="$emit('input','')"/>
        </div>
    </div>
</template>

<script>
export default {
    name: 'BlockLink',
    data:()=>({
        link: ''
    }),
    computed:{
        stile(){
            return ''
            //return `top:${this.$attrs.coords.top}px;left:${this.$attrs.coords.left};`
        }
    },
    mounted(){
        
        this.link = this.$attrs.link
        // let coords = this.$refs.editorLink.getBoundingClientRect()
        // this.$emit('position',coords.height)
        // if ( coords.right > window.innerWidth - 200 ){
        //     this.$refs.editorLink.style.left = coords.left - 100 + 'px'
        // }
    }
}
</script>