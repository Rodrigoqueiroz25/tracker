<template>
    <Box>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroComp :tempo-em-segundos="tarefa.duracao" />
            </div>
        </div>
    </Box>

</template>

<script lang="ts">
import ITarefa from "@/interfaces/ITarefa";
import { defineComponent, PropType } from "vue";
import CronometroComp from "./CronometroComp.vue";
import Box from "./Box.vue";

export default defineComponent({
    name: "TarefA",

    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    },

    components: { CronometroComp, Box }
})
</script>

<style scoped>
.box {
    background: #FAF0CA;
}
</style>