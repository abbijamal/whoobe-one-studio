<template>
        <div class="overflow-x-hidden">
            <div class="overflow-y-auto flex flex-col">
            <BlockContainer 
                v-if="doc" 
                :doc="doc" 
                :key="doc.id" 
                id="content"/>
            </div>
        </div>
</template>

<script>
export default {
    name:'PreviewFrame',
    components:{
        'BlockContainer' : () => import ( './BlockContainer.vue')
    },
    computed:{
        doc(){
            document.querySelector('meta[name="viewport"]').setAttribute("content",  "width=368,initial-scale=1.0") 
            this.$store.dispatch ( 'preview' , true )
            return JSON.parse(window.localStorage.getItem('whoobe-preview'))
        }
    }
}
</script>
<style>
    body { overflow-y: auto; }
</style>
