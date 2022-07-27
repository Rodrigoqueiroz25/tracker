<template>
    <div class="box has-text-weight-bold">
        <slot></slot> <!--o que tiver entre a abaertura e fechamento de tag do componente redenriza aqui-->
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    export default defineComponent({
        name: "BoxB",
    
    })

</script>

<style scoped>
.box {
    background: #FAF0CA;
}
</style>