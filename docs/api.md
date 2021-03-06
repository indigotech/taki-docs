# API

If you are looking for a detailed endpoint documention, you can check our Swagger [here](https://app.swaggerhub.com/apis/askmon/Taki/1.0.0).

## Introduction

The Taki API will be used by the SDKs to send device and user information to our servers. It will also be used by the client side to send user information (that are not accessible by the SDKs) and the campaigns to be created.

## User information

Here is an explanation of each field we expect to receive with user informations:

- `identifier` - string that will identify the user, like CPF, user id, etc.
- `topics` - data that will be used to segment the push notification, for example: `abandoned_cart` topic, when the user left products in the app cart without buying
- `data` - these data are used to create customizable push notification content

## Campaign information

A campaign consists of a set of rules that are used to send segmented push notifications for the users.

- `name` - campaign identifier
- `topic` - the topics to which the push notifications will be sent
- `title` - push notification title
- `message` - push notification message
- `customPayload` - custom information that will be sent along with the notification, the app will have to know how to handle it
- `quarantine` - if the user already received a notification from this campaign, he'll only receive another from the same campaign after the quarantine time passes
- `userQuarantine` - like quarantine, but user won't receive pushes from any campaign until this time passes
- `periodicity` - time used to repeat the notification sending process for the campaign
- `initialDate` - date to start the campaign
- `endDate` - date to end the campaign