# Disclaimer

Copied from: [github.com/dsmiller95/custom-emoji-server](https://github.com/dsmiller95/custom-emoji-server) I just hacked in some stuff to see if it would work and that is now the POC. You'll notice stuff in the gets for /emoticons and /emoticon endpoints.

# Emoji server

## Setup

This app is configured to be hosted on heroku, with a postgress server alongside it. It's likely you can get it to work hosted elsewhere. All it needs is the connection to a postgres server with this single table: `emoji(id: integer, name: text, image: bytea)`

## API

### GET `/emoticons`

Returns a json aray of all valid emoticons names. EX:

```json
["parrot", "partyparrot", "chucknorris"]
```

### GET `/emoticon/emoticonName`

Returns the raw image data for the emoticon with the name emoticonName

If not found, returns a 404

### POST `/emoticon/emoticonName`

Post the raw image data to this endpoint, and an emoticon with the name emoticonName will be created. If "emoticonName" already exists, nothing changes

### DELETE `/emoticon/emoticonName`

Self-explanatory. if emoticonName exists, deletes it. Otherwise returns 200