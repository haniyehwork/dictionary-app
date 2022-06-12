<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal">
            <slot></slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: [],
    methods:{
        closeModal(){
            this.$emit('close')
        }
    }
    
}
</script>



<style scoped>
    .modal{
        width: 400px;
        padding: 4%;
        margin: 100px auto;
        background: rgb(143, 143, 193);
        border-radius: 20px;
    }
    .backdrop{
        top: 0;
        position: fixed;
        background: #33333373;
        width: 100%;
        height: 100%;
    }
    h1{
        color: rgb(40, 26, 68);
    }
    
</style>