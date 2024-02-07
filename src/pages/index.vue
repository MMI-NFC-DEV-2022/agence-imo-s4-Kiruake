<template>

  <!-- //avec valeur en attributs
  
  <AfficheMaison nomMaison="Maison" image="src/assets/img/ImageMaison.jpg"/>
  
  //avec v-bind
  
  <AfficheMaison v-bind="maMaison"/> -->
  
  avec v-bind tableaux
  
  <AfficheMaison v-bind="Maisons[0]"/>
    <AfficheMaison v-bind="Maisons[1]"/>
    <AfficheMaison v-bind="Maisons[2]"/>
  
  </template>
  
  <script setup lang="ts">
  
  import AfficheMaison from '@/components/AfficheMaison.vue';
  // import { SchemaOffreMaison } from '../types.ts';
  
  // const maMaison :SchemaOffreMaison = {
  //   nomMaison: "Maison",
  //   nbrChambres: 3,
  //   nbrSDB: 2,
  //   prix: 200000,
  //   adresse: "2 Rue de la maison",
  //   image: "src/assets/img/ImageMaison.jpg",
  //   surface: "30x40",
  //   favori: false,
  
  // }
  
  const Maisons = [
      {
  id: '2',
  nomMaison: 'Maison22',
  prix: 1234,
  favori: true,
  image: '',
  nbrChambres: 22,
  nbrSDB: 22,
  adresse: '1234 rue',
  surface: '1234',
  
      },
  
      {
  id: '3',
  nomMaison: 'Maison33',
  prix: 12345,
  favori: true,
  image: '',
  nbrChambres: 33,
  nbrSDB: 33,
  adresse: '12345 rue',
  surface: '12345',
      },
  
      {
  id: '4',
  nomMaison: 'Maison44',
  prix: 123456,
  favori: true,
  image: '',
  nbrChambres: 44,
  nbrSDB: 44,
  adresse: '123456 rue',
  surface: '123456',
      }
  ];
  
  
  </script>