<template>
    <div class="overflow-x-auto w-full">
    <table class="table">
        <!-- head -->
        <thead>
        <tr>
            <th></th>
            <th>Proyectos</th>
            <th>Tareas</th>
            <th>Avance</th>
        </tr>
        </thead>

        <tbody>
        <!-- row 2 -->
        <tr v-for="(project, index) in projectStore.projectList" :key="project.id" class="hover:bg-base-300">
            <th>{{ index + 1 }}</th>
            <td>{{ project.nomen }}</td>
            <td>{{ project.chores.length }}</td>
            <progress class="progress progress-primary w-56" value="10" max="100"></progress>
        </tr>
        
        </tbody>
    </table>

</div>

<InputModal 
    :aperta="modalAperta" ç
    @claudere="modalAperta=false"
    @valorem="projectStore.addereProject"
    placejolder="Introduce el nombre del proyecto"
    titulus="Nuevo proyecto"
    subtitulus="Dale un nombre a tu proyecto"
/>

<proprium-modal :aperta="PropriumModalAperta">

    <template #header>
        <h1 class="text-3xl">Título del modal</h1>
    </template>

    <template #body>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestiae eligendi illum voluptatum optio eaque placeat. Temporibus porro aliquid repellendus, maiores eum quisquam voluptas eveniet vel odio soluta eius quas eaque.</p>
    </template>

    <template #footer>
        <div class="flex justify-end">
            <button @click="PropriumModalAperta=false" class="btn">Close</button>
            <button @click="PropriumModalAperta=false" class="btn btn-primary ml-4">Aceptar</button>
        </div>
    </template>

</proprium-modal>


<fab-button @click="modalAperta = true">
    <AddCircle/>
</fab-button>

<fab-button @click="PropriumModalAperta = true" positione="bottom-left">
    <ModalIcon/>
</fab-button>

</template>


<script lang="ts" setup>
    import FabButton from '@/modulorum/commune/components/FabButton.vue';
    import InputModal from '@/modulorum/commune/components/InputModal.vue';
    import PropriumModal from '@/modulorum/commune/components/PropriumModal.vue';
    import AddCircle from '@/modulorum/commune/icons/AddCircle.vue';
    import ModalIcon from '@/modulorum/commune/icons/ModalIcon.vue';
    import { ref } from 'vue';
    import { useProjectsStore } from '../stores/projects.store';



    const modalAperta= ref(false);
    const PropriumModalAperta= ref(false);

    const projectStore = useProjectsStore();

</script>