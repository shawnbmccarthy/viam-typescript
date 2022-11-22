# viam-typescript

Simple Viam Typescript example

## Setup 

### install buf
[buf installation](https://docs.buf.build/installation)

### Project Setup

```sh
npm install
npm run buf-google
npm run buf-stream
npm run buf-api
```

### setup environment

create and add below to .env file 
```shell
VITE_VIAM_ROBOT_PAYLOAD="<ROBOT_SECRET>"
VITE_VIAM_ROBOT_ADDRESS="<ROBOT_ADDR>"
VITE_VIAM_SIGNAL_HOST="https://app.viam.com:443"
VITE_VIAM_ICE_SERVER="stun:global.stun.twilio.com:3478?transport=udp"
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```
