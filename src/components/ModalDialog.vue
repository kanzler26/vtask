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
              <v-text-field
                v-model="fields.name"
                label="Name"
                hint="example of helper text only on focus"
              >
              </v-text-field>
            </v-col>
            <v-col cols="12" sm="6" md="4">
              <v-text-field
                v-model="fields.lastName"
                label="Lastname"
                persistent-hint
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="6" md="4">
              <v-text-field
                label="Group name"
                required
                v-model="fields.groupName"
              ></v-text-field>
            </v-col>
          </v-row>
        </v-container>
      </v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="blue darken-1" text @click="ChangeDialogActivator">
          Close
        </v-btn>
        <v-btn color="blue darken-1" text @click="Save">
          Save
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>
<script>

export default {
  props: {
    value: {
      type: Boolean,
      default: () => false,
    },
    group: {
      type: Object,
      default: () => null,
    },
  },
  data: () => ({
    dialog: false,
    fields: {},
  }),
  watch: {
    value: {
      immediate: true,
      handler() {
        this.dialog = this.value;
      },
    },
    group() {
      if (this.group) {
        this.fields = { ...this.group };
      }
    },
    dialog() {
      this.$emit("input", this.dialog); //передаём значение в родительский компонент
    },
  },
  methods: {
    ChangeDialogActivator() {
      this.dialog = false;
    },
    CheckWhatInValue(evn) {
      console.log(evn);
    },
    Save(){
      this.$emit('onSave', {...this.fields})
      this.$emit("input", false);
    }
  },
};
</script>