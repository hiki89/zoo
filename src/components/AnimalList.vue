<template>
  <div>
    <h1>ZOO</h1>
    
    <form @submit.prevent>
        <label>Species: </label>
        <input v-model="newAnimal.species" type="text" placeholder="Species"> <br>
        <label>Name: </label>
        <input v-model="newAnimal.name" type="text" placeholder="Name"> <br>
        <label>Date of Birth: </label>
        <input v-model="newAnimal.dateOfBirth" type="text" placeholder="Date of Birth"> <br>
        <label>Sector: </label>
        <select v-model="newAnimal.sector" placeholder="select sector">
            <option disabled="" selected="">Select sector</option>
            <option v-for="(sector, index) in sectors"
             :key="index" v-bind:value="sector">{{sector.name}}</option>
        </select> <br>
        <button @click="addAnimal" type="submit">Add Animal</button>
    </form>

    <table align="center">
        <thead>
            <th>Species</th>
            <th>Name</th>
            <th>Date of birth</th>
            <th>Sector</th>
            <th>Surface</th>
        </thead>
        <tbody>
            <tr v-for="(animal, index) in animals" :key="index" 
                v-bind:style="[animal.background ? {'background':'lightgreen'} : {'background': 'white'}]">
                <td>{{animal.species}}</td> 
                <td>{{animal.name}}</td> 
                <td v-if="animal.dateOfBirth !== ''">{{animal.dateOfBirth}}</td> 
                <td v-else>Nepoznato</td> 
                <td>{{animal.sector.name}}</td> 
                <td>{{animal.sector.surface}}</td> 
                <td>
                    <button @click="deleteAnimal(animal)">Delete</button>
                </td>
                <td>
                    <button @click="toggleBackground(animal)">Background</button>
                </td>
                <td v-if="animals.indexOf(animal) !== 0">
                    <button  @click="moveToTop(animal)">Move to top</button>
                </td>
            </tr>
        </tbody>
    </table>

    <table align="center">
        <thead>
            <th>Sectors</th>
        </thead>
        <tbody>
            <tr v-for="(sector, index) in sectors" :key="index">
                <td>{{sector.name}}</td>
                <td>
                    <button @click="showAnimals(sector)">Show animals</button>
                </td>
            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
const sectors = [
    {name: "predator", surface: "cage"},
    {name: "reptile", surface: "glass box"}
];
export default {
  name: 'AnimalList',
  data() {
      return {
          sectors: sectors,
          animals: [
              {species: "cameleon", name: "Marko", dateOfBirth: "1.1.2018", sector: sectors[1], background: true},
              {species: "lizard", name: "Nikola", dateOfBirth: "2.1.2018", sector: sectors[1], background: false},
              {species: "bear", name: "Meda", dateOfBirth: "3.1.2018", sector: sectors[0], background: true},
              {species: "lion", name: "Maca", dateOfBirth: "4.1.2018", sector: sectors[0], background: false},
              {species: "puma", name: "Dzon", dateOfBirth: "5.1.2018", sector: sectors[0], background: true},
              {species: "tiger", name: "Milica", dateOfBirth: '', sector: sectors[0], background: false}
          ],
          newAnimal: {
              background: true
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
          this.newAnimal = {
              background: true
            };
      },

      showAnimals(sector) {
          const animalList = [];
          this.animals.forEach(animal => {
              if(animal.sector.name === sector.name) {
                  animalList.push(`${animal.species} ${animal.name}`);
              }
          });
          alert(animalList);
      },

      toggleBackground(animal) {
            if (animal.background === true) {
                animal.background = false;
            } else {
                animal.background = true;
            }
      }
  }
}
</script>