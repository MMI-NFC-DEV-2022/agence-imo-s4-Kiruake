<script setup lang="ts">
import { ref} from '@vue/reactivity';
import { FormKit } from '@formkit/vue';
import type { SchemaOfMaison } from '@/type';
const maison = ref<SchemaOfMaison>({});
import { supabase } from '@/supabase';

async function upsertMaison(dataForm, node) {
 const { data, error } = await supabase.from("Maison").upsert(dataForm).select();
 if (error) node.setErrors([error.message])
}
</script>

<template>
  
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