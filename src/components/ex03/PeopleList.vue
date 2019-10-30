<template>
  <div class="card-content">
    <b-field label="แสดงรายชื่อทั้งหมด" v-if="people.length">
      <b-table :data="people" :selected.sync="selected" focusable>
        
         <template slot-scope="props">

                <b-table-column label="รหัสนักศึกษา">
                    {{ props.row.stdid }}
                </b-table-column>

                <b-table-column label="คำนำหน้า">
                    {{ props.row.title }}
                </b-table-column>

                <b-table-column label="ชื่อ">
                    {{ props.row.firstName }}
                </b-table-column>

                <b-table-column label="นามสกุล">
                    {{ props.row.lastName }}
                </b-table-column>

                <b-table-column label="X" :data="people" :selected.sync="selected" focusable>
                    <b-button type="is-danger" @click="deletePerson">Delete</b-button>
                </b-table-column>

                
            </template>
        
        </b-table>
    </b-field>
    

  </div>
</template>
<script>
import { mapState } from "vuex";

export default {

  created() {
    this.$store.dispatch("people/getPeople");
  },

  data() {
    return {
      selected: {},
      columns: [
        { field: "title", label: "คำนำหน้า" },
        { field: "firstName", label: "ชื่อ" },
        { field: "lastName", label: "นามสกุล" },
        { field: "isActive", label: "Active" }
      ]
    };
  },
  computed: {
    ...mapState("people", ["people"])
  },
  methods: {
    deletePerson() {
      this.$store.dispatch("people/deletePerson", this.selected );
    }
  }
};
</script>