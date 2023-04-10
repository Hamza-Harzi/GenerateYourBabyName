<script setup lang="ts">
import { Gender, Popularity, Length, names } from "@/data";
//use typeScript to define the types of our variables
//utilise reactive in order to have a state of object
interface OptionsState {
  // we're going to define the type of each key value pair
  gender: Gender;
  popularity: Popularity;
  length: Length;
}

const options = reactive<OptionsState>({
  //our state
  gender: Gender.GIRL,
  length: Length.ALL,
  popularity: Popularity.UNIQUE,
});

//we want to compute all of the different name that is belonging to the categories that were selected
//hachti bil names fih majmou3a min string fi west array

//we need figure out all of the names that belong to the category that our state is currently in
const computedSelectedNames = () => {
  const filteredName = names
    .filter((name) => name.gender === options.gender)
    .filter((name) => name.popularity === options.popularity)
    .filter((name) => {
      if (options.length === Length.ALL) return true;
      else return name.length === options.length;
    });

  selectedNames.value = filteredName.map((name) => name.name);
};

const selectedNames = ref<string[]>([]);

//this function is to remove name
const removeName = (index: number) => {
  const filtereNames = [...selectedNames.value];
  filtereNames.splice(index, 1);
  selectedNames.value = filtereNames;
};
const optionArray = [
  {
    title: "1) Choose a gender",
    category: "gender",
    buttons: [Gender.GIRL, Gender.UNISEX, Gender.BOY],
  },
  {
    title: "2) Choose the name's popularity",
    category: "popularity",
    buttons: [Popularity.TRENDY, Popularity.UNIQUE],
  },
  {
    title: "3) Choose name's length",
    category: "length",
    buttons: [Length.SHORT, Length.ALL, Length.LONG],
  },
];
</script>

<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" buttom below</p>
    <div class="options-container">
      <Option
        v-for="option in optionArray"
        :key="option.title"
        :option="option"
        :options="options"
      />
      <button class="primary" @click="computedSelectedNames">Find Names</button>
    </div>
    <div class="cards-container">
      <!-- <div v-for="name in selectedNames" :key="name" class="card">
        <h4>{{ name }}</h4>
        <p>x</p>
      </div> -->
      <CardName
        v-for="(name, index) in selectedNames"
        :key="name"
        :name="name"
        @remove="() => removeName(index)"
        :index="index"
      />
    </div>
  </div>
</template>

<style scoped>
.container {
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(27, 60, 138);
  max-width: 50rem;
  margin: 0 auto;
  text-align: center;
}
h1 {
  font-size: 3rem;
}
.options-container {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 1rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
}

.primary {
  background-color: rgb(249, 87, 89);
  color: white;
  border-radius: 6.5rem;
  border: none;
  padding: 0.75rem 4rem;
  font-size: 1rem;
  margin-top: 1rem;
  cursor: pointer;
}

.cards-container {
  display: flex;
  margin-top: 3rem;
  flex-wrap: wrap;
}

/* 209*/
</style>
