0.5.5 / 2017-11-01
==================
### messaging-api-messenger
- [new] Added [`passThreadControlToPageInbox`](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-messenger#handover-protocol-api) method:

```js
client.passThreadControlToPageInbox(USER_ID);
```

is equivalent to

```js
client.passThreadControl(USER_ID, 263902037430900);
```

See more details in [Messenger docs](https://developers.facebook.com/docs/messenger-platform/handover-protocol/pass-thread-control#page_inbox).

0.5.4 / 2017-10-30
==================
### messaging-api-line
- [new] Introducing new Rich Menu APIs!
  + [getRichMenuList](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-line#getrichmenulist)
  + [getRichMenu](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-line#getrichmenurichmenuid)
  + [createRichMenu](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-line#createrichmenurichmenu)
  + [deleteRichMenu](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-line#deleterichmenurichmenuid)
  + [getLinkedRichMenu](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-line#getlinkedrichmenuuserid)
  + [linkRichMenu](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-line#linkrichmenuuserid-richmenuid)
  + [unlinkRichMenu](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-line#unlinkrichmenuuserid)
  + [downloadRichMenuImage](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-line#downloadrichmenuimagerichmenuid)
  + [uploadRichMenuImage](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-line#uploadrichmenuimagerichmenuid-buffer)

See more details in [LINE Official docs](https://developers.line.me/en/docs/messaging-api/reference/#rich-menu).

0.5.3 / 2017-10-26
==================
### messaging-api-messenger
- [fix] return null when no any messenger profile setting exists [#176](https://github.com/Yoctol/messaging-apis/issues/176)

0.5.2 / 2017-10-26
==================
- [deps] Upgrade `axios` to `v0.17.0`.

0.5.1 / 2017-10-25
==================
### messaging-api-messenger
- [renamed] Following profile methods has been renamed to match api key:
  + `getGetStartedButton` -> `getGetStarted`
  + `setGetStartedButton` -> `setGetStarted`
  + `deleteGetStartedButton` -> `deleteGetStarted`
  + `getGreetingText` -> `getGreeting`
  + `setGreetingText` -> `setGreeting`
  + `deleteGreetingText` -> `deleteGreeting`
  + `getChatExtensionHomeURL` -> `getHomeURL`
  + `setChatExtensionHomeURL` -> `setHomeURL`
  + `deleteChatExtensionHomeURL` -> `deleteHomeURL`

The deprecated methods will be removed after `v0.6.0`.

0.5.0 / 2017-10-20
==================
- [new] A big improvement on error message.

For example, when you catch the error and log it out:

```js
client.sendText().catch(console.error);
```

You can get some useful information to help you resolve the issue.

```
Error: Messenger API - 2500 OAuthException An active access token must be used to query information about the current user.
    at handleError (/Users/chentsulin/Projects/yoctol/ttt/node_modules/messaging-api-messenger/lib/MessengerClient.js:64:9)
    at <anonymous>
    at process._tickCallback (internal/process/next_tick.js:188:7)

Error Message -
  Messenger API - 2500 OAuthException An active access token must be used to query information about the current user.

Request -
  POST https://graph.facebook.com/v2.10/me/messages?access_token=

Request Data -
  {
    "recipient": {
      "id": ""
    },
    "message": {
      "text": ""
    }
  }

Response -
  400 Bad Request

Response Data -
  {
    "error": {
      "message": "An active access token must be used to query information about the current user.",
      "type": "OAuthException",
      "code": 2500,
      "fbtrace_id": "GOnNuiN/ewZ"
    }
  }
```

The error messages are powered by [axios-error](https://github.com/Yoctol/messaging-apis/tree/master/packages/axios-error) package.

- [deprecated] `client.getHTTPClient()` method is deprecated. use `client.axios` getter instead.

### messaging-api-messenger
- [breaking] `client.version` now return version number string (`2.10`) instead of the v-prefix version (`v2.10`).

0.4.7 / 2017-10-16
==================
### messaging-api-viber
- [fix] Always throw error when status != 0 in api response body.

0.4.6 / 2017-10-15
==================
### messaging-api-telegram
- [new] Support methods introduced in Telegram 3.4
  + [editMessageLiveLocation](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-telegram#editmessagelivelocationlocation--options---official-docs)
  + [stopMessageLiveLocation](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-telegram#stopmessagelivelocationoptions---official-docs)
  + [setChatStickerSet](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-telegram#setchatstickersetchatid-stickersetname---official-docs)
  + [deleteChatStickerSet](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-telegram#deletechatstickersetchatid---official-docs)

See more details in [Telegram October 11, 2017 changelog](https://core.telegram.org/bots/api#october-11-2017).

0.4.5 / 2017-10-12
==================
### messaging-api-viber
- [new] implement getAccountInfo, getUserDetails, getOnlineStatus:
  + [`getAccountInfo`](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-viber#getaccountinfo)
  + [`getUserDetails(id)`](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-viber#getuserdetailsid)
  + [`getOnlineStatus(ids)`](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-viber#getonlinestatusids)

0.4.4 / 2017-10-11
==================
### messaging-api-messenger
- [renamed] `getDomainWhitelist` -> `getWhitelistedDomains`
- [renamed] `setDomainWhitelist` -> `setWhitelistedDomains`
- [renamed] `deleteDomainWhitelist` -> `deleteWhitelistedDomains`

### messaging-api-viber
- [new] First release of [Viber](https://www.viber.com/) API Support!

0.4.3 / 2017-09-28
==================
### messaging-api-line
- [new] Added a [LINE Bot example](https://github.com/Yoctol/messaging-apis/tree/master/examples/line). Thanks @madeinfree!

### messaging-api-telegram
- [new] Gets [Payments API](https://github.com/Yoctol/messaging-apis/tree/master/packages/messaging-api-telegram#payments-api) support! 🎉
  + `sendInvoice`
  + `answerShippingQuery`
  + `answerPreCheckoutQuery`

0.4.2 / 2017-09-22
==================
### messaging-api-messenger
- [new] Export version of Graph API:

```js
const { MessengerClient } = require('messaging-api-messenger');

const client = MessengerClient.connect(accessToken);

client.version; // "v2.10"
```

0.4.1 / 2017-09-19
==================
### messaging-api-line
- [fix] Wrong case in filename.

0.4.0 / 2017-09-19
==================
### messaging-api-messenger
- [breaking] Renamed `send` to `sendMessage`

### messaging-api-line
- [breaking] Renamed all of `LINE` to PascalCase `Line` (follow convention from other modules), e.g. `LineClient.connect`, `Line.createText`.

Example:

```js
const { Line, LineClient } = require('messaging-api-line');
```

0.3.5 / 2017-09-15
==================
### messaging-api-messenger
- [docs] Fix a typo.

### messaging-api-line
- [new] Support message factories:
  + LINE.createText
  + LINE.createImage
  + LINE.createVideo
  + createAudio
  + createLocation
  + createSticker
  + createImagemap
  + createTemplate
  + createButtonTemplate
  + createConfirmTemplate
  + createCarouselTemplate
  + createImageCarouselTemplate

For example:

```js
const { LINE } = require('messaging-api-line');

client.reply(REPLY_TOKEN, [
  LINE.createText('Hello'),
  LINE.createImage(
    'https://example.com/original.jpg',
    'https://example.com/preview.jpg'
  ),
  LINE.createText('End'),
]);
```


0.3.4 / 2017-09-13
==================
- [docs] Show method arguments in tables.

### messaging-api-messenger
- [new] Support message batching via `sendBatch`:

```js
const { Messenger } = require('messaging-api-messenger');

client.sendBatch([
  Messenger.createText(USER_ID, '1'),
  Messenger.createText(USER_ID, '2'),
  Messenger.createText(USER_ID, '3'),
  Messenger.createText(USER_ID, '4'),
  Messenger.createText(USER_ID, '5'),
]);
```

0.3.3 / 2017-09-07
==================
- publish docs changes to npm.

0.3.2 / 2017-09-05
==================
### messaging-api-line
- [new] Support ImageCarouselTemplate methods
  + replyImageCarouselTemplate
  + pushImageCarouselTemplate
  + multicaseImageCarouselTemplate

0.3.1 / 2017-08-31
==================
### messaging-api-messenger
- [new] using `AttachmentPayload` to send cached attachment:

```js
client.sendImage(USER_ID, { attachment_id: '55688' });
client.sendAudio(USER_ID, { attachment_id: '55688' });
client.sendVideo(USER_ID, { attachment_id: '55688' });
client.sendFile(USER_ID, { attachment_id: '55688' });
```

0.3.0 / 2017-08-29
==================
- [docs] A big improvement.

### messaging-api-messenger
- [breaking] Renamed messenger typing methods:

```
turnTypingIndicatorsOn => typingOn
turnTypingIndicatorsOff => typingOff
```
- [breaking] Removed tagged template methods:
  + sendTaggedTemplate
  + sendShippingUpdateTemplate
  + sendReservationUpdateTemplate
  + sendIssueResolutionTemplate
  + sendAppointmentUpdateTemplate
  + sendGameEventTemplate
  + sendTransportationUpdateTemplate
  + sendFeatureFunctionalityUpdateTemplate
  + sendTicketUpdateTemplate

Use `tag` option instead:

```js
client.sendText(USER_ID, 'Hello!', { tag: 'ISSUE_RESOLUTION' });

client.sendGenericTemplate(
  USER_ID,
  [
    {
      // ...
    },
  ],
  { tag: 'ISSUE_RESOLUTION' }
);
```
- [breaking] Renamed `topElementStyle` to `options.top_element_style` in `sendListTemplate` [@6840ec7](https://github.com/Yoctol/messaging-apis/commit/6840ec7094be6c0f6c0a9d995b3756b86f4f5f17)
- [breaking] Renamed `ratio` to `options.image_aspect_ratio` in `sendGenericTemplate` [@701e717](https://github.com/Yoctol/messaging-apis/commit/701e717abe8b8f1de63d5c3f9c49e601fc9cacc0)

### messaging-api-slack
- [breaking] Removed `SlackClient` export, using `SlackOAuthClient` or `SlackWebhookClient` instead.
- [breaking] `getUserList` now returns object includes cursor.

### messaging-api-telegram
- [breaking] Changed `contact.firstName` to `contact.first_name`, and `contact.phoneNumber` to `contact.phone_number` in `sendContact` method.

0.2.8 / 2017-08-25
==================
### messaging-api-messenger
- [new] Support `mark_seen` sender action:

```js
client.markSeen(USER_ID);
```

0.2.7 / 2017-08-17
==================
### messaging-api-telegram
- [new] Implement supergroup or channel methods
  + `kickChatMember`
  + `unbanChatMember`
  + `restrictChatMember`
  + `promoteChatMember`
  + `exportChatInviteLink`
  + `setChatPhoto`
  + `deleteChatPhoto`
  + `setChatTitle`
  + `setChatDescription`
  + `pinChatMessage`
  + `unpinChatMessage`
  + `leaveChat`


0.2.6 / 2017-08-14
==================
### messaging-api-messenger
- [new] Support calling send API with recipient object:

```js
client.sendText(
  {
    phone_number: '+1(212)555-2368',
    name: { first_name: 'John', last_name: 'Doe' },
  },
  'Hello World'
);
```

- [new] Support send media (sendAudio、sendImage、sendVideo、sendFile) using `Buffer` or `ReadStream`:

```js
client.sendImage(USER_ID, buffer);
client.sendFile(USER_ID, fs.createReadStream('LookGreatToMe.pdf'));
```

### messaging-api-slack
- [docs] Added Slack OAuth API document

0.2.5 / 2017-08-09
==================
### messaging-api-messenger
- [new] Implement Page Messaging Insights API
- [new] Implement Bulit-in NLP API

### messaging-api-slack
- [new] Slack OAuth Client

0.2.4 / 2017-08-02
==================
- [docs] A big improvement.
- [docs] prettify code examples with prettier

### messaging-api-messenger
- [new] Chat Extension Home URL API
- [new] Messenger Code API
- [new] Handover Protocol APIs
- [new] add 5 new tagged templates
- [deps] upgrade default graph api version to `v2.10`

### messaging-api-line
- [new] LINE Group/Room Member API

0.2.3 / 2017-07-13
==================
### messaging-api-telegram
- [new] Add optional parameters to telegram api [#47](https://github.com/Yoctol/messaging-apis/pull/47).
- [new] Implement get methods
  + `getUserProfilePhotos`
  + `getFile`
  + `getChat`
  + `getChatAdministrators`
  + `getChatMembersCount`
  + `getChatMember`
- [new] Implement updating methods
  + `editMessageText`
  + `editMessageCaption`
  + `editMessageReplyMarkup`
  + `deleteMessage`
- [new] `forwardMessage` method


0.2.2 / 2017-07-11
==================
- [deps] Update `lerna` to `v2.0.0`.

### messaging-api-messenger
- [new] Support send open graph template with `MessengerClient.sendOpenGraphTemplate`.

### messaging-api-telegram
- [new] First release.


0.2.1 / 2017-07-06
==================
- [new] Add `engines` in `package.json` [#38](https://github.com/Yoctol/messaging-apis/pull/38).
- [new] Setup test coverage report using `codecov` .

### messaging-api-messenger
- [fix] Fix wrong checking rules in `sendQuickReplies` methods.

### messaging-api-line
- [fix] `retrieveMessageContent` should return `Promise<Buffer>`.

### messaging-api-slack
- [new] First release.


0.2.0 / 2017-06-29
==================
- [docs] rewrite new docs for Messenger & LINE
- [breaking] APIs now return detail data and not just an `axios` response.
- [breaking] rename `factory` to `connect`

### messaging-api-messenger
- [new] support use specified graph api version
- [new] support menu locale
- [new] support greeting locale
- [breaking] rename `inputDisabled` to `composerInputDisabled`

### messaging-api-line
- [new] support more `reply` methods and `multicast` methods
