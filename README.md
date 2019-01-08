# Bitrix24Parser
Birtri24Parser - easiest way to parse webhook data from Bitrix24 and form outcoming payload

## How to use
1. Require necessary method from parser.js
2. Set incoming data from Bitrix24 webhook as variable
3. Select on of available methods from "parser" object and call it with bitrix24 webhook data as function params

#### Discord webhook usage example
 ```
const {data, payload, embeds} = require('parser')

  let const webhookData

  let incomingLeadId = data(webhookData).leadId
  let payload = parser.payload('Name', 'channel_id', 'token', 'avatar', 'guild_id', 'id', `Text message`)
  let payload = parser.embeds(`Message text`, URL, Bitrix Domain)
 ```

## "data" method 

  Contains webhook data parts.

  * leadId  - webhook lead ID number
  * bitrixDomain - webhook bitrix domain informtion
  * ts - webhook timestamp
  * clientEndpoint - webhook client endpoint
  * serverEndpoint -  webhook server endpoint
  * memberId - webhook member ID
  * applicationToken - application token

  ```
  let incomingBitrixDomain = data(webhookData).bitrixDomain
  let incomingMemberId = data(webhookData).memberId

  ```

## "payload" method
  "Payload" will form valid payload form from params, that you pass to it
  
  ```
  parser.payload(name, channelId, token, avatar, guildId, id, content) {
  return {
    'name': name,
    'channel_id': channelId, 
    'token': token
    'avatar': avatar
    'guild_id': guildId
    'id': id
    'content': content 
  }
}
  ```
  ! "Content" field must contain message. 

## "embeds" method
  "Embeds" will form valid embed form form params, that you pass to it

  ```
  parser.embeds = function (title, url, name) {
  return { 'embeds': [
    {
      'title': title,
      'url': url,
      'author': {
        'name': name
      }
    }
  ] }
}
  ```
  ! "Title" fild must contain message.

## License

[MIT](LICENSE)