<script land="ts">
    import Tag from './Tag.vue';

    export default {
        props: {
            ingrediente: {type: String, required: true}
        },
        components: {Tag},
        data() {
            return {
                selecionado : false
            }
        },
        methods: {
            aoClicar() {
                this.selecionado = !this.selecionado;

                if (this.selecionado) {
                    this.$emit('adicionarIngrediente', this.ingrediente);
                }
            }
        },
        emits: ['adicionarIngrediente'] // declarando eventos personalisado que o componente emite
    }  
</script>

<template>
    <button class="ingrediente" v-on:click="aoClicar()" :aria-pressed="selecionado"> <!-- v-on pode ser substituido por @click -->
        <Tag :texto="ingrediente" :ativa="selecionado" />
    </button>
</template>

<style scoped>
    .ingrediente {
        cursor: pointer;
    }
</style>