<template>
  <v-dialog v-model="dialog" max-width="600px">
    <v-card>
      <v-card-title>
        <span class="text-h5">User Profile</span>
      </v-card-title>
      <v-card-text>
        <v-container>
          <v-row>
            <v-col cols="12" sm="6" md="4">
              <v-text-field label="Group name*" required></v-text-field>
            </v-col>
            <v-col cols="12" sm="6" md="4">
              <v-text-field
                label="Name"
                hint="example of helper text only on focus">ffsfs
               </v-text-field>
            </v-col>
            <v-col cols="12" sm="6" md="4">
              <v-text-field
                label="Lastname*"
                hint="example of persistent helper text"
                persistent-hint
                required
              >fgghgf444</v-text-field>
            </v-col>
          </v-row>
        </v-container>
        <small>*indicates required field</small>
      </v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="blue darken-1" text @click="dialog = false">
          Close
        </v-btn>
        <v-btn color="blue darken-1" text @click="dialog = false"> Save </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>
<script>

export default {
  
  props: {
    value: {
      activator: Boolean,
      item: {
        name: String,
        lastName: String,
        groupName: String,
      },
    },
  },
  data: () => ({
    dialog: false,
  }),
  watch: {
    value: {
      immediate: true,
      handler() {
        console.log(this.value.item.name + " :console");
        this.dialog = this.value;
      },
    },
  },
};
</script>