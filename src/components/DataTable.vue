<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="groups"
      :items-per-page="5"
      @click:row="callDialog"
      class="elevation-1"
    ></v-data-table>
    <ModalDialog v-model="dialog" :group="groupData" @onSave="Save" />
  </div>
</template>
<script>
import { groups, headers } from "@/utils/util";
import ModalDialog from "@/components/ModalDialog.vue";

export default {
  components: {
    ModalDialog,
  },
  name: "App",
  data: () => ({
    dialog: false,
    groups: groups,
    headers: headers,
    groupData: {},
    indexInObj: null,
  }),
  methods: {
    callDialog(event, { item, index }) {
      this.groupData = item;
      this.indexInObj = index;
      this.dialog = !this.dialog;
    },
    Save(fields) {
      this.groups[this.indexInObj] = Object.assign(this.groupData, fields);
    },
  },
};
</script>