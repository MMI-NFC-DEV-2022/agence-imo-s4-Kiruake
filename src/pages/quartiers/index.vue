<script setup lang="ts">
import { supabase } from "../../supabase";

const { data, error } = await supabase.from('quartiercommune').select();

//const { data, error } = await supabase.from('Quartier').select('Nom, id, Commune(id, Nom)');
//if (error) console.log("n'a pas pu charger la table quartier_commune :", error);


const group = Object.groupBy(data, v => v.NomCommune)
console.log("group :", group);
</script>

<template>
    <section class="flex flex-col">
        <h3 class="text-2xl">Liste des quartiers</h3>
        <ul>
            <li v-for="(les_quartiers, NomCommune) in group">
                <!-- {{ quartierObject.Commune.Nom }} -
        {{ quartierObject.Nom }} -->
                <h4 class=" font-bold pt-3">{{ NomCommune }}</h4>
                <ul>
                    <li class="p-4 bg-blue-600     " v-for="quartierObject in les_quartiers">
                        {{ quartierObject.nom_quartier }}
                    </li>
                </ul>
            </li>
        </ul>
    </section>
</template>