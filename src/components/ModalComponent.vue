<script setup>
// Define component properties
const props = defineProps({
  // Modal's heading (default: empty string)
  title: {
    type: String,
    default: "",
  },
  // List of ingredients (default: empty array)
  ingredients: {
    type: Array,
    default: () => [],
  },
  // Preparation steps for the drink (default: empty array)
  instructions: {
    type: Array,
    default: () => [],
  },
  // Alternative mocktail recipe (default: empty string)
  mocktail: {
    type: String,
    default: "",
  },
  // Suggested glass type for the drink (default: empty string)
  glassware: {
    type: String,
    default: "",
  },
});

// Enable component to emit events to parent
const emit = defineEmits();

// Close the modal
const closeModal = () => {
  emit("close-modal");
};
</script>

<template>
  <!-- Modal background overlay -->
  <div class="modal-overlay">
    <!-- Close modal button -->
    <button @click="closeModal" class="close-button">
      <!-- Close button icon -->
      <img
        src="https://assets.24g.com/public/2022-frontend-test-project/exit_icon.svg"
        alt="Close"
      />
    </button>

    <!-- Modal content container -->
    <div class="modal">
      <!-- Modal title section -->
      <div class="heading-modal">
        <h2 class="text-container">{{ title }}</h2>
      </div>

      <!-- Ingredients list -->
      <section class="ingredients-section">
        <h3>Ingredients:</h3>
        <ul>
          <!-- Display each ingredient -->
          <li v-for="ingredient in ingredients" :key="ingredient">
            {{ ingredient }}
          </li>
        </ul>
      </section>

      <!-- Preparation instructions -->
      <section class="instructions-section">
        <h3>Instructions:</h3>
        <ol>
          <!-- Display each preparation step -->
          <li v-for="instruction in instructions" :key="instruction">
            {{ instruction }}
          </li>
        </ol>
      </section>

      <!-- Mocktail alternative section -->
      <section class="mocktail-section">
        <h3>Make it a mocktail:</h3>
        <span>{{ mocktail }}</span>
      </section>

      <!-- Suggested glass type section -->
      <section class="glassware-section">
        <h3>Glassware</h3>
        <span>{{ glassware }}</span>
      </section>
    </div>
  </div>
</template>

<style scoped>
@import "../assets/style.css";
</style>
