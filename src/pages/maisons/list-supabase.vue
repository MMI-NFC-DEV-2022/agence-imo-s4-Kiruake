<script setup lang="ts">

import { supabase } from "@/supabase";
console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code
const maisons = []; // à remplacer par l'appel à Supabase

let { data, error } = await supabase
    .from('maison')
    .select('*');


</script>

<template>
    <h1>Liste de la Supabase</h1>
</template>