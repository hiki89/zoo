<template>
  <div>
    <h1>Animals</h1>

    <table align="center">
        <thead>
            <th>Speaces</th>
            <th>Name</th>
            <th>Date of birth</th>
        </thead>
        <tbody>
            <tr v-for="(animal, index) in animals" :key="index">
                <td>{{animal.speaces}}</td> 
                <td>{{animal.name}}</td> 
                <td>{{animal.dateOfBirth}}</td> 
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
              {speaces: "reptiles", name: "cameleon", dateOfBirth: "1.1.2018"},
              {speaces: "birds", name: "eagle", dateOfBirth: "2.1.2018"},
              {speaces: "mammals", name: "bear", dateOfBirth: "3.1.2018"},
              {speaces: "fish", name: "shark", dateOfBirth: "4.1.2018"},
              {speaces: "insects", name: "ant", dateOfBirth: "5.1.2018"}
          ]
      };
  }
}
</script>