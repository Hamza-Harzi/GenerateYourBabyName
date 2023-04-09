<template>
  <div class="option-container">
    <h4>1) Choose a gender</h4>
    <div class="option-buttons">
      <button
        class="option option-left"
        :class="options.gender === Gender.BOY && 'option-active'"
        @click="options.gender = Gender.BOY"
      >
        Boy
      </button>
      <button
        class="option"
        :class="options.gender === Gender.UNISEX && 'option-active'"
        @click="options.gender = Gender.UNISEX"
      >
        Unisex
      </button>
      <button
        class="option option-right"
        :class="options.gender === Gender.GIRL && 'option-active'"
        @click="options.gender = Gender.GIRL"
      >
        Girl
      </button>
    </div>
  </div>
</template>

<!-- <div class="option-container">
    <h4>2) Choose the name's popularity</h4>
    <div class="option-buttons">
      <button
        class="option option-left"
        :class="options.popularity === Popularity.TRENDY && 'option-active'"
        @click="options.popularity = Popularity.TRENDY"
      >
        Trendy
      </button>
      <button
        class="option option-right"
        :class="options.popularity === Popularity.UNIQUE && 'option-active'"
        @click="options.popularity = Popularity.UNIQUE"
      >
        Unique
      </button>
    </div>
  </div>
  <div class="option-container">
    <h4>2) Choose name's length</h4>
    <div class="option-buttons">
      <button
        class="option option-left"
        :class="options.length === Length.LONG && 'option-active'"
        @click="options.length = Length.LONG"
      >
        Long
      </button>
      <button
        class="option"
        :class="options.length === Length.ALL && 'option-active'"
        @click="options.length = Length.ALL"
      >
        All
      </button>
      <button
        class="option option-right"
        :class="options.length === Length.SHORT && 'option-active'"
        @click="options.length = Length.SHORT"
      >
        Short
      </button>
    </div> -->
