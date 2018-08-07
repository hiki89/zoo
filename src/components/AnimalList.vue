<template>
  <div>
    <h1>Animals</h1>

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
          ]
      };
  }
}
</script>