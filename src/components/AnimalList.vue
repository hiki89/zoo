<template>
  <div>
    <h1>Animals</h1>
    
    <form @submit.prevent>
        <label>Species: </label>
        <input v-model="newAnimal.species" type="text" placeholder="Species"> <br>
        <label>Name: </label>
        <input v-model="newAnimal.name" type="text" placeholder="Name"> <br>
        <label>Date of Birth: </label>
        <input v-model="newAnimal.dateOfBirth" type="text" placeholder="Date of Birth"> <br>
        <button @click="addAnimal" type="submit">Add Animal</button>
    </form>

    <table align="center">
        <thead>
            <th>Species</th>
            <th>Name</th>
            <th>Date of birth</th>
        </thead>
        <tbody>
            <tr v-for="(animal, index) in animals" :key="index">
                <td>{{animal.species}}</td> 
                <td>{{animal.name}}</td> 
                <td v-if="animal.dateOfBirth !== ''">{{animal.dateOfBirth}}</td> 
                <td v-else>Nepoznato</td> 
                <td> <button @click="deleteAnimal(animal)">Delete</button></td>
                <td v-if="animals.indexOf(animal) !== 0"> <button  @click="moveToTop(animal)">Move to top</button></td>
            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data() {
      return {
          animals: [
              {species: "reptiles", name: "cameleon", dateOfBirth: "1.1.2018"},
              {species: "birds", name: "eagle", dateOfBirth: "2.1.2018"},
              {species: "mammals", name: "bear", dateOfBirth: "3.1.2018"},
              {species: "fish", name: "shark", dateOfBirth: "4.1.2018"},
              {species: "insects", name: "ant", dateOfBirth: "5.1.2018"},
              {species: "birds", name: "owl", dateOfBirth: ''}
          ],
          newAnimal: {

          }
      };
  },

  methods: {
      deleteAnimal(animal) {
        let indexOfAnimalToDelete = this.animals.indexOf(animal);
        this.animals.splice(indexOfAnimalToDelete, 1);
      },

      moveToTop(animal) {
        this.deleteAnimal(animal);
        this.animals.unshift(animal);  
      },

      addAnimal() {
          this.animals.push(this.newAnimal);
          this.newAnimal = {};
      }
  }
}
</script>