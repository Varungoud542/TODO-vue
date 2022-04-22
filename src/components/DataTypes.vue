<script>
export default {
  name: "DataType",
  data() {
    return {
      name: "varun",
      numb: 1,
      member: {
        name: "varun",
        age: "20",
        color: "white",
      },
      familys: [
        { name: "varun", age: 20 },
        { name: "sucharitha", age: 28 },
        { name: "tinku", age: 26 },
      ],
    };
  },
};
</script>
<template>
  <div>String: {{ name }}</div>
  <div>Number: {{ numb }}</div><br/>
  <div>{{ member.name }} {{ member.age }} {{ member.color }}</div>
  <div v-for="(family, index) in familys">
    <div>{{ index+1 }}.{{ family.name }}-{{ family.age }}</div>
  </div>
</template>
