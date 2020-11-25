# gapi

> A thin Node wrapper for [Google's client-side javascript V3 API](https://apis.google.com/js/api.js) with TypeScript declaration.

## Example

```bash
npm install --save gapi-client

yarn add gapi-client
```

`index.js:`

```javascript
import gapi from '@ganesshkumar/gapi';

gapi.load('client:auth2', () => {
  gapi.client.init({
    discoveryDocs: ["<discoveryDocs_corresponding_to_the_APIs_you_use>"],
    clientId: '<your_client_id>',
    scope: '<scope_you_want_to_add>'
  }).then(function () {
    // do stuff with loaded APIs
    gapi.auth2.getAuthInstance().isSignedIn.listen(updateSigninStatus);
    updateSigninStatus(gapi.auth2.getAuthInstance().isSignedIn.get());
  });
});

const updateSigninStatus = (isSignedIn) => {
  if (isSignedIn) {
    console.log('User is signed in')
  } else {
    console.log('User is not signed in')
  }
}

// To trigger the sign in flow, you can call the following function from appropriate place.
gapi.auth2.getAuthInstance().signIn();
```

## TypeScript

This repo has the basic support for TypeScript.

## License

[Apache-2.0](./LICENSE)

