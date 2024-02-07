<script setup lang="ts">
import { ref} from '@vue/reactivity';
import { FormKit } from '@formkit/vue';
import type { SchemaOfMaison } from '@/type';
const maison = ref<SchemaOfMaison>({});
import { supabase } from '@/supabase';
import AfficheMaison from './AfficheMaison.vue';
import { useRouter, useRoute } from 'vue-router/auto';
const router = useRouter();

async function upsertMaison(dataForm, node) {
 const { data, error } = await supabase.from("Maison").upsert(dataForm).select("id");
 if (error) node.setErrors([error.message])
 else{
    console.log("data :", data);}
    router.push({name:'/maisons/edit/[[id]]', params: {id: data[0].id}});
}

const route = useRoute('/maisons/edit/[[id]]');
if (route.params.id) {
    const { data, error } = await supabase.from("Maison").select("*").eq("id", route.params.id).single();
    if (error) console.error("error", error);
    else maison.value = data;
}
</script>

<template>

    <div class="p-2">
        <h2 class="text-2xl">Résultat (prévisualisation)</h2>
        <AfficheMaison v-bind="maison" />
    </div>


  
    <div class="p-2">
        <FormKit type="form" v-model="maison" @submit="upsertMaison">
            <FormKit name="nomMaison" label="nom" type="text" />
            <FormKit name="prix" label="prix" type="number"/>
            <FormKit name="surface" label="surface" type="textarea"/>
            <FormKit name="adresse" label="adresse" type="text"/>
            <FormKit name="nbrSDB" label="nombre de SDB" type="number"/>
            <FormKit name="nbrChambres" label="nombre de chambres" type="number"/>
            <FormKit name="favori" label="Mettre en valeur" type="checkbox"/>

        </FormKit>
        </div>
    
</template>

<style>

label {
    display: block;
    margin-bottom: 0.5rem;
}

input[type="text"],
input[type="number"],
textarea {
    width: 100%;
    padding: 0.5rem;
    margin-bottom: 1rem;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    padding: 0.5rem 1rem;
    background-color: #000;
    color: #000;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #333;
}



</style>