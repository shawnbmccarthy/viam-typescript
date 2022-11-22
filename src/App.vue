<script setup lang="ts">
import {onMounted, ref} from 'vue'
import {dialWebRTC} from '@viamrobotics/rpc'

const signalHost = ref(import.meta.env.VITE_VIAM_SIGNAL_HOST)
const robotPayload = ref(import.meta.env.VITE_VIAM_ROBOT_PAYLOAD)
const robotHost = ref(import.meta.env.VITE_VIAM_ROBOT_ADDRESS)
const iceServer = ref(import.meta.env.VITE_VIAM_ICE_SERVER)

let webRTCConn: any

onMounted(async () => {
  try {
    webRTCConn = await dialWebRTC(
        signalHost.value,
        robotHost.value,
        {
          authEntity: robotHost.value,
          credentials: {
            type: 'robot-location-secret',
            payload: robotPayload.value
          },
          webrtcOptions: {
            disableTrickleICE: false,
            signalingAuthEntity: robotHost.value,
            signalingCredentials:  {type: 'robot-location-secret', payload: robotPayload.value},
            rtcConfig: {
              iceServers: [{urls: iceServer.value}]
            }
          }
        }
    )
  } catch(err) {
    console.error(`failed to connect: ${err}`)
  }
  console.log(`webrtcconn: ${webRTCConn}`)
})
</script>

<template>
</template>

<style scoped>
</style>
