`<script setup lang="ts">
import { supabase, user } from '../supabase';
</script>
<template>
<div>
    <button id="deco" v-if="user" @pointerdown="supabase.auth.signOut()">
        Se déconnecter ({{user.email}})
    </button>
    <button id="co" v-else @pointerdown="supabase.auth.signInWithOAuth({provider: 'github'})">
        Se connecter avec Github
    </button>
</div>
</template>   

<style>

#co {
    background-color: #000;
    color: #fff;
    padding: 1rem;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

#deco {
    background-color: #fff;
    color: #000;
    padding: 1rem;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

</style>