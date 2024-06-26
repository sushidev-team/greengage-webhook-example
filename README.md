# Example for Using the Webhook of greengage API

## Before you start

Make sure you replace SECRET_KEY in the given code examples with your secret.

## Curl

```bash
curl --location --request POST 'https://api-stage.greengage.dev/webhooks' \
--header 'Authorization: SECRET_KEY' \
--header 'Content-Type: application/json' \
--data-raw '{ "origin":"mindearth", "type": "create", "data": { "name":"Test", "starting_point" : [45.46464374888545, 9.18934835519496], "description": "It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using <Content here, content here>, making it look like readable English.", "duration_min": 5, "distance_mt": 1200, "deeplink": "URL HERE", "external_id": 18, "active": true, "poi_id":"778d6b3b-f1f6-4efc-a703-b687044e7f36" } }'
```

For duration two different attributes can be used:

"duration" or "duration_min"

## Poi = Point of interest

The Greengage APP requires a "poi_id" parameter which will be used to display it in the app.

To get a list of POI use the following curl request:

```
curl --location --request POST 'https://api-stage.greengage.dev/graphql' \
--header 'Authorization: q4Rqm7KBWitMcu_@' \
--header 'Origin: http://localhost:3000' \
--header 'Content-Type: application/json' \
--data-raw '{"query":"{\n    pois {\n        id\n        title\n    }\n}","variables":{}}'
```

## Browser

Open the example code [index.html](index.html). Please be aware for sake of simplicity we are using alpinejs + vanilla js in this example. For testing run the following command:

```sh
npm i && npx http-server -p 3000
```

## Examples for status change

```bash
curl --location --request POST 'https://api-stage.greengage.dev/webhooks' \
--header 'Authorization: SECRET_KEY' \
--header 'Content-Type: application/json' \
--data-raw '{ "origin":"mindearth", "type": "update", "data": { "external_id": "18", "status": "PENDING" } }'
```

Possible status updates:

- OPEN
- PENDING
- FAILED
- FINISHED

Please be aware that the update mechanism of the mission can contain every property of the above. (CREATE)


## Pass the user id

Every request can contain a user_id (from green) which identifies the user that opened the task.
It will be appended if requested.