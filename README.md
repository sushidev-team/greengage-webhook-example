# Example for Using the Webhook of greengage API

## Before you start

Make sure you replace SECRET_KEY in the given code examples with your secret.

## Curl

```bash
curl --location --request POST 'https://api-stage.greengage.dev/webhooks' \
--header 'Authorization: SECRET_KEY' \
--header 'Content-Type: application/json' \
--data-raw '{ "origin":"mindearth", "data": { "name":"Test", "starting_point" : [45.46464374888545, 9.18934835519496], "description": "It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using <Content here, content here>, making it look like readable English.", "duration_min": 5, "distance_mt": 1200 } }'
```

## Browser

Open the example code [index.html](index.html). Please be aware for sake of simplicity we are using alpinejs + vanilla js in this example. For testing run the following command:

```sh
npm i && npx http-server -p 3000
```