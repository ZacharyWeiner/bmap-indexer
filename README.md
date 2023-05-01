# bmap-api

This API is hosted publicly at https://b.map.sv

It is a Bitcoin transaction indexer and API for building 'BMAP' Bitcoin apps. It uses [junglebus](https://junglebus.gorillapool.io) to crawl for transactions and transforms them with [bmapjs](https://bmapjs.com). It runs two processes:

## Crawler

A crawler and indexer that saves transaction data into a MongoDB database.

## API

API Was moved to seperate repo rohenaz/bmap-api

# Install

### Prerequisites

Docker & Docker-Compose

### Run Locally

Install dependencies

```bash
yarn
```

Start the app (make sure your env vars are set first)

```bash
yarn start
```

### Run in docker

Build the image

```bash
docker build -t bmap-api.
```

Start the app
`bash
docker-compose up

````

### Configuration

`config.js` hold config values.

Set the `from` value to the block to begin indexing.

#### Install MongoDB

To run locally you will need mongodb installed.

See their [installation guide](https://docs.mongodb.com/manual/installation)

# Config

Set the following environmental variables:

- `MONGO_URL` A connection string to your mongo database. ex: mongodb://127.0.0.1:27017/bmap when running locally, or mongodb://mongo:27017/bmap from within a container.

# Run

```bash
node index
````

# More Examples

[MAP.app = TonicPow](https://b.map.sv/query/ewogICJ2IjogMywKICAicSI6IHsKICAgICJmaW5kIjogewogICAgICAiTUFQLmFwcCI6ICJ0b25pY3BvdyIKICAgIH0sCiAgICAic29ydCI6IHsgImJsay5pIjogLTEgfSwKICAgICJsaW1pdCI6IDEwCiAgfQp9)

[BITPIC.paymail = satchmo@moneybutton.com](https://b.map.sv/query/ewogICJ2IjogMywKICAicSI6IHsKICAgICJmaW5kIjogewogICAgICAiQklUUElDLnBheW1haWwiOiAic2F0Y2htb0Btb25leWJ1dHRvbi5jb20iCiAgICB9LAogICAgImxpbWl0IjogMTAKICB9Cn0=)

[BITKEY.paymail = satchmo@moneybutton.com](https://b.map.sv/query/ewogICJ2IjogMywKICAicSI6IHsKICAgICJmaW5kIjogewogICAgICAiQklUS0VZLnBheW1haWwiOiAic2F0Y2htb0Btb25leWJ1dHRvbi5jb20iCiAgICB9LAogICAgImxpbWl0IjogMTAKICB9Cn0=)

With BitQuery you can search in all sorts of ways.

#### Records within the last 24 hours:

1. Set a timestamp in the expected format.

```js
let timestamp = Math.floor(new Date().getTime() / 1000 - 86400)
```

2. Search for records since that timestamp:

```json
{
  "v": 3,
  "q": {
    "blk.t": { "$gt": <timestamp> }
  }
}
```

# BMAPjs

This API returns data in BMAP format which is a derivative of [BOB](https://github.com/interplanaria/bpu):
[BMAPjs](https://github.com/rohenaz/bmap)

[bmapjs.com](https://bmapjs.com)
