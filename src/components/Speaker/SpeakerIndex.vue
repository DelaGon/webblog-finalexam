<template>
  <div>
    <h1>Get All Speaker </h1>
    <div>Speaker {{ speakers.length }}</div>
    <div v-for="speaker in speakers" v-bind:key="speaker.id">
      <div>id: {{ speaker.id }}</div>
      <div>model: {{ speaker.name }} - {{ speaker.lastname }}</div>
      <div>Brand: {{ speaker.email }}</div>
      <div>Watt: {{ speaker.password }}</div>
      <p>
        <button v-on:click="navigateTo('/speaker/' + speaker.id)">
          ดูข้อมูลSpeaker
        </button>
        <button v-on:click="navigateTo('/speaker/edit/' + speaker.id)">
          แกไขข้อมูล
        </button>
        <button v-on:click="deletespeaker(speaker)">ลบข้อมูล</button>
      </p>
      <hr />
    </div>
  </div>
</template>
<script>
import SpeakerServices from "@/services/SpeakerService";
export default {
  data() {
    return {
      speakers: []
    };
  },
  methods: {
    navigateTo(route) {
      this.$router.push(route);
    },
    async deleteSpeaker(speaker) {
      let result = confirm("Want to delete?");
      if (result) {
        try {
          await SpeakerServices.delete(speaker);
          this.refreshData()
        } catch (err) {
          console.log(err);
        }
      }
    },
    async refreshData() {
      this.speakers = (await SpeakerServices.index()).data;
    }
  },
  async created() {
    this.speakers = (await SpeakerServices.index()).data;
  }
};
</script>
<style scoped></style>
