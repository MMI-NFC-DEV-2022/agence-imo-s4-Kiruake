<script setup lang="ts">
import { ref} from '@vue/reactivity';
import AfficheMaison from '@/components/AfficheMaison.vue';
import { FormKit } from '@formkit/vue';
import type { SchemaOfMaison } from '@/type';
const maison = ref<SchemaOfMaison>({});
import { supabase } from '@/supabase';
import Form from '@/components/Form.vue';

async function upsertMaison(dataForm, node) {
 const { data, error } = await supabase.from("Maison").upsert(dataForm).select();
 if (error) node.setErrors([error.message])
}
</script>

<template>

  

        <Form />

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