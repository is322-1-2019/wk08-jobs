<template>
  <div class="card-content">
    <nav-bar></nav-bar>
    <person-form class="card"></person-form>
    <people-list class="card"></people-list>
    <active-people-list class="card"></active-people-list>
  </div>
</template>
<script>
import PersonForm from "./PersonForm.vue";
import PeopleList from "./PeopleList.vue";
import ActivePeopleList from "./ActivePeopleList.vue";
import NavBar from "../NavBar.vue";

export default {
  components: {
    PersonForm,
    PeopleList,
    ActivePeopleList,
    NavBar,
  }
}
</script>