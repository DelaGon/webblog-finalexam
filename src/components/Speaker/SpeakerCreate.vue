<template>
  <div>
    <h1>Create Speakers</h1>
    <form v-on:submit.prevent="createSpeaker">
      <p>model: <input type="text" v-model="speaker.name" /></p>
      <p>Brand: <input type="text" v-model="speaker.brand" /></p>
      <p>Watt: <input type="text" v-model="speaker.watt" /></p>
      <p>power_input: <input type="text" v-model="speaker.power" /></p>
      <p>status: <input type="text" v-model="speaker.status" /></p>
      <p>type: <input type="text" v-model="speaker.type" /></p>
      <p><button type="submit">create speaker</button></p>
    </form>
    <hr />
    <div>
      <div>model: {{ speaker.name }}</div>
      <div>Brand: {{ speaker.brand }}</div>
      <div>Watt: {{ speaker.watt }}</div>
      <div>power_input:{{ speaker.power }}</div>
      <div>status:{{ speaker.status }}</div>
      <div>type:{{ speaker.type }}</div>
    </div>
  </div>
</template>
<script>
import SpeakersService from "@/services/speakerService";

export default {
  data() {
    return {
      model: "",
      brand: "",
      watt: "",
      power_input: "",
      status: "activity",
      type: ""
      }
    };
  },
  methods: {
    async createSpeaker() {
      try {
        await SpeakerService.post(this.speaker);
        this.$router.push({
          name: "speakers"
        });
      } catch (err) {
        console.log(err);
      }
    }
  }
};
