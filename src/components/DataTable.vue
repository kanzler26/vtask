<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="groups"
      :items-per-page="5"
      @click:row="callDialog"
      class="elevation-1"
    ></v-data-table>
    <VDialogTest v-model="dialog" />
  </div>
</template>
<script>
import objArr from "@/utils/util";
import VDialogTest from "@/components/VDialog.vue";

export default {
  components: {
    VDialogTest,
  },
  name: "App",
  data: () => ({
    dialog: true,
    groups: objArr.groups,
    headers: objArr.headers,
  }),
  methods: {
    callDialog(item, ctx) {
      this.dialog = true
      console.log(item);
      console.log(ctx);
    },
  },
};
</script>