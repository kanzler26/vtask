<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="groups"
      :items-per-page="5"
      @click:row="callDialog"
      class="elevation-1"
    ></v-data-table>
    <ModalDialog v-model="groupData" />
  </div>
</template>
<script>
import objArr from "@/utils/util";
import ModalDialog from "@/components/ModalDialog.vue";

export default {
  components: {
    ModalDialog,
  },
  name: "App",
  data: () => ({
    dialog: false,
    groups: objArr.groups,
    headers: objArr.headers,
    groupData: {},
  }),
  methods: {
    callDialog(event, idx) {
      this.dialog = !this.dialog;
      this.groupData = {
        value: this.dialog,
        item: {
          name: idx.item.name,
          lastName: idx.item.lastName,
          group: idx.item.groupName,
        },
      };
    },
  },
};
</script>