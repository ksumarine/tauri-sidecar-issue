<template>
  <div>
    <a @click="OnSidecarTest">Click me</a>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { Command } from "@tauri-apps/api/shell";
export default defineComponent({
  name: "App",
  methods: {
    async OnSidecarTest() {
      const cmd = Command.sidecar("bin/ffmpeg", ["-version"]);
      const out = await cmd.execute();
      console.log(out.stdout);
    },
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
