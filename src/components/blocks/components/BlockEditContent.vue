<template>
    <div id="contentEditor" ref="contentEditor" class="flex flex-col items-start w-64" v-if="$store.state.editor.current">
        <!-- <div class="p-1 bg-gray-200 w-full">Edit content</div> -->
        <div v-if="$store.state.editor.current.tag === 'youtube' || $store.state.editor.current.tag === 'vimeo'">
            <label>Video ID</label>
            <input class="m-1" type="text" v-model="$store.state.editor.current.content" placeholder="video ID only"/>
        </div>
        <div v-else>
            <textarea v-if="$store.state.editor.current.element != 'p' && $store.state.editor.current && $store.state.editor.current.element!='img'" class="p-1 h-40 w-full  text-base" v-model="$store.state.editor.current.content"/>
        </div>
        <!-- <button class="m-2" v-if="$store.state.editor.current.element === 'p'">Advanced Editor</button> -->
        <!-- <BlockTipTap v-if="$store.state.editor.current.element === 'p'" v-model="$store.state.editor.current.content"></BlockTipTap> -->
    </div>
</template>

<script>
export default {
    name: 'BlockEditContent',
    components: {
        'BlockTipTap' : () => import ( '@/components/blocks/components/BlockTipTap.vue' )
    },
    computed:{
        stile(){
            return ''
            return 'top:' + this.$attrs.coords.top + 'px;left:' + this.$attrs.coords.left + 'px;resize:both;'
        }
    },
    mounted(){
        let coords = this.$refs.contentEditor.getBoundingClientRect()
        this.$emit('position',coords.height)
        if ( coords.right > window.innerWidth - 200 ){
            this.$refs.contentEditor.style.left = coords.left - 200 + 'px'
        }
        if ( this.$store.state.editor.current.element === 'p' ){
            this.$dialogBus ( 'TipTapEditor')
        }
        // if ( this.$store.state.editor.current ){
        //     let el = document.getElementById('contentEditor')
        //     let coords = el.getBoundingClientRect()
        //     console.log ( coords )
        // }
    }
}
</script>