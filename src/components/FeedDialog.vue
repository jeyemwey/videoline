<template>
  <v-dialog
      v-model="dialog"
      width="500"
    >

    <template v-slot:activator="{ on }">
      <slot name="dialog-activator" v-bind:on="on"></slot>
    </template>

    <v-card>
      <v-card-title
        class="headline grey lighten-2"
        primary-title
      >
        Add Channel Feed
      </v-card-title>

      <v-card-text>
        <v-text-field v-model="channelId" prefix="https://youtube.com/channel/" placeholder="YouTube channel ID"/>
      </v-card-text>

      <v-divider></v-divider>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn
          color="primary"
          text
          @click="feedSubmit"
        >
          Add
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: 'FeedDialog',
  data: () => ({
    dialog: false,
    channelId: '',
  }),
  methods: {
    feedSubmit() {
      this.$emit('feedSubmitted', this.channelId);
      this.dialog = false;
      this.channelId = '';
    },
  },
};
</script>
