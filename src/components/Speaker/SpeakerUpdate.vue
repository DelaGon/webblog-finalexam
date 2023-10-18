<template>
  <div>
    <h1> Speaker</h1>
    <div>id: {{ speaker.id }}</div>
      <div>id: {{ speaker.id }}</div>
      <div>model: {{ speaker.name }}</div>
      <div>Brand: {{ speaker.brand }}</div>
      <div>Watt: {{ speaker.watt }}</div>
      <div>power_input:{{ speaker.power }}</div>
      <div>status:{{ speaker.status }}</div>
      <div>type:{{ speaker.type }}</div>
  </div>
</template>
<script>
import SpeakerService from "@/services/SpeakerService";

export default {
  data() {
    return {
      speaker: null
    };
  },
  async created() {
    let speakerId = this.$route.params.speakerId;
    this.speaker = (await speakerService.show(speakerId)).data
    console.log(this.speakerId)
  }
};
</script>
<style scoped></style>
