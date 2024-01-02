<script setup>
// Importing necessary utilities and assets
import { ref } from "vue"; // Importing 'ref' for creating reactive references.
import drinksJson from "/src/assets/drinks.json";
import ModalComponent from "@/components/ModalComponent.vue";

// Reactive data for the selected drink's details.
const drinkTitle = ref(""); // Title of the selected drink.
const drinkIngredients = ref([]); // Ingredients of the selected drink.
const drinkInstructions = ref([]); // Instructions for the selected drink.
const mocktail = ref(""); // Mocktail version information.
const glassware = ref(""); // Recommended glassware.
const isOpen = ref(false); // Modal visibility control.

/**
 * Updates and displays the modal with details of the selected drink.
 *
 * @param {Object} drink - The drink object containing its details.
 */
function showModal(drink) {
  drinkTitle.value = drink.name;
  drinkIngredients.value = drink.ingredients;
  drinkInstructions.value = drink.steps;
  mocktail.value = drink.mocktail;
  glassware.value = drink.glassware;
  isOpen.value = true; // Display the modal.
}
</script>

<template>
  <!-- Modal display, active only when isOpen is true -->
  <div>
    <ModalComponent
      v-if="isOpen"
      :title="drinkTitle"
      :ingredients="drinkIngredients"
      :instructions="drinkInstructions"
      :mocktail="mocktail"
      :glassware="glassware"
      @close-modal="isOpen = false"
    />
  </div>

  <!-- Header containing company logo and introductory text -->
  <div class="header">

    <!-- logo -->
    <!-- Comment 
    <img
      src="https://ibb.co/nn5d46B" 
      alt="Logo"
      class="logo"
    /> -->

    <!-- Introductory text section -->
    <div class="text-container">
      <h1 class="heading-text">Welcome Holiday Text</h1>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla rhoncus
        odio ac ante malesuada feugiat. Mauris pretium, nulla ac imperdiet
        suscipit, nibh enim pellentesque sapien, ut hendrerit dolor sapien
        gravida lacus.
      </p>
    </div>
  </div>

  <!-- Container showcasing available drinks -->
  <div class="drinks-container">
    <!-- Loop through each drink and display its image; on click, show its details in modal -->
    <div
      class="drink-grid"
      v-for="drink in drinksJson.drinks"
      :key="drink.id"
      @click="showModal(drink)"
    >
      <div class="drink-card">
        <img :src="drink.images.front" alt="Front Image" class="drink front" />
        <!-- To display the back image of the drink -->
        <!-- <img :src="drink.images.back" alt="Back Image" class="drink back"> -->
      </div>
    </div>
  </div>
</template>

<style>
/* Import main stylesheet for the component */
@import "./assets/style.css";
</style>
