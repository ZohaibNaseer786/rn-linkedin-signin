<p align="center">
    <img alt="rn-linkedin-signin" src="https://zohaib-personal.s3.amazonaws.com/linkedin.gif" width=250>
</p>

<h3 align="center">
  🔗 React-Native LinkedIn Signin
</h3>
<p align="center">
Simple <strong>LinkedIn</strong> login library for <strong>React-Native</strong> with <i>WebView</i> into a <i>Modal</i>
</p>
<p align="center">
  <a href="#hire-an-expert"><img src="https://img.shields.io/badge/%F0%9F%92%AA-hire%20an%20expert-brightgreen"/></a>
  <a href="https://gfycat.com/weepygratefulfairyfly"><img src="https://img.shields.io/badge/reactnative.gallery-%F0%9F%8E%AC-green.svg"></a>
  <a href="https://www.npmjs.com/package/react-native-linkedin"><img src="https://badge.fury.io/js/react-native-linkedin.svg"></a>
  <a href="https://www.npmjs.com/package/react-native-linkedin"><img src="https://img.shields.io/npm/dm/react-native-linkedin.svg?style=flat-square"></a>
  <a href="https://travis-ci.org/xcarpentier/react-native-linkedin"><img src="https://travis-ci.org/xcarpentier/react-native-linkedin.svg?branch=master"></a>
</p>

<br />

## Benefits

- **Light**: No need to link a native library like others alternatives
- **Simple**: Get the token and the expires, you handle your own login with the access_token
- **Sure**: open-source
- **Almost readable & understandable code**: JavaScript & React

## Installation

```bash
$ yarn add rn-linkedin-signin
$ yarn add react-native-webview
```

## Security

Please note that you should give your linkedin client id but not your secret key to this component.
You should be aware that key can be found if you store it directly to your code.
**I strongly recommend to not declare client secret key on your code but found a way to keep it secret**

- [> Related issue]()
- [> LinkedIn Documentation](https://docs.microsoft.com/en-us/linkedin/shared/api-guide/best-practices/secure-applications?context=linkedin/context#api-key-and-secret-key)

```tsx
  <LinkedinSignin
    shouldGetAccessToken={false}
    clientSecret={null}
    clientID="[ Your client id from https://www.linkedin.com/developer/apps ]"
    redirectUri="[ Your redirect uri set into https://www.linkedin.com/developer/apps ]"
    onSuccess={{ authentication_code } => console.log(`Post this ${authentication_code} to your server.`)}
  />
```

## Example

```JavaScript
// See ./App.tsx file for details
import React from 'react'
import { StyleSheet, View } from 'react-native'

import LinkedinSignin from 'rn-linkedin-signin'

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    justifyContent: 'center',
    alignItems: 'center',
  },
})

export default class AppContainer extends React.Component {
  linkedRef = React.createRef<LinkedinSignin>()
  render() {
    return (
      <View style={styles.container}>
        <LinkedinSignin
          ref={this.linkedRef}
          clientID="[ Your client id from https://www.linkedin.com/developer/apps ]"
          clientSecret="[ Your client secret from https://www.linkedin.com/developer/apps ]"
          redirectUri="[ Your redirect uri set into https://www.linkedin.com/developer/apps ]"
          onSuccess={token => console.log(token)}
        />
        <Button title="Log Out" onPress={this.linkedRef.current.logoutAsync()} />
      </View>
    )
  }
}
```

## Props

| Name                     | Type                          | Required                                                                              | Default                             | Description                                                                                                                                                                                              |
| ------------------------ | ----------------------------- | ------------------------------------------------------------------------------------- | ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| clientID                 | string                        | **required**                                                                          |                                     | [Your client id](https://www.linkedin.com/developer/apps)                                                                                                                                                |
| <s>clientSecret</s>      | string                        | use **shouldGetAccessToken={false}** and read **authorization_code** onSuccess return |                                     | Should not be stored in app [WARNING! Your client secret](https://docs.microsoft.com/en-us/linkedin/shared/api-guide/best-practices/secure-applications?context=linkedin/context#api-key-and-secret-key) |
| redirectUri              | string                        | **required**                                                                          |                                     | [Your redirectUri](https://www.linkedin.com/developer/apps)                                                                                                                                              |
| onSuccess                | function                      | **required**                                                                          |                                     | Function will be call back on success                                                                                                                                                                    |
| authState                | string                        | optional                                                                              | `require('uuid').v4()`              | The state of auth, to be more secure                                                                                                                                                                     |
| onError                  | function                      | optional                                                                              | `console.error(err)`                | Function will be call back on error                                                                                                                                                                      |
| onClose                  | function                      | optional                                                                              |                                     | Function will be call back on close modal                                                                                                                                                                |
| onOpen                   | function                      | optional                                                                              |                                     | Function will be call back on open modal                                                                                                                                                                 |
| onSignIn                 | function                      | optional                                                                              |                                     | Function will be call back when the user sign in                                                                                                                                                         |
| permissions              | array                         | optional                                                                              | `'r_liteprofile', 'r_emailaddress'` | The LinkedIn access token permissions                                                                                                                                                                    |
| renderButton             | function                      | optional                                                                              |                                     | Render function for customize LinkedIn button                                                                                                                                                            |
| renderClose              | function                      | optional                                                                              |                                     | Render function for customize close button                                                                                                                                                               |
| linkText                 | string                        | optional                                                                              | `'Login with LinkedIn'`             | Link label                                                                                                                                                                                               |
| containerStyle           | ViewPropTypes.style           | optional                                                                              |                                     | Customize container style                                                                                                                                                                                |
| wrapperStyle             | ViewPropTypes.style           | optional                                                                              |                                     | Customize wrapper style                                                                                                                                                                                  |
| closeStyle               | ViewPropTypes.style           | optional                                                                              |                                     | Customize close style                                                                                                                                                                                    |
| animationType            | Modal.propTypes.animationType | optional                                                                              | `fade`                              | Customize animationType style: 'none', 'slide' or 'fade'                                                                                                                                                 |
| **shouldGetAccessToken** | bool                          | optional                                                                              | `true`                              | Set to false to receive the 'authorization code' rather then the 'access token'                                                                                                                          |
| areaTouchText | object      | optional       | `{top: 20, bottom: 20, left: 50, right: 50}`          | Set values for to increase the text touch area          |

## Contribution

- [@xcarpentier](mailto:contact@xaviercarpentier.com)

**PRs are welcome!**

## FAQ

### Is it supported and tested both on android and iOS?

**YES**

### How to logout rn-linkedin-signin?
```tsx
<View style={styles.container}>
    <LinkedinSignin
      ref={this.linkedRef}
      clientID="[ Your client id from https://www.linkedin.com/developer/apps ]"
      clientSecret="[ Your client secret from https://www.linkedin.com/developer/apps ]"
      redirectUri="[ Your redirect uri set into https://www.linkedin.com/developer/apps ]"
      onSuccess={token => console.log(token)}
    />
    <Button title="Log Out" onPress={this.linkedRef.current.logoutAsync()} />
</View>
```


## Other questions

Feel free to [contact me](mailto:zohaibnaseer2244@gmail.com) or [create an issue](https://github.com/ZohaibNaseer786/react-native-linkedin-signin/issues)

## Alternatives

- [react-native-linkedin-login](https://www.npmjs.com/package/react-native-linkedin-login)
- [react-native-linkedin-sdk](https://www.npmjs.com/package/react-native-linkedin-sdk)
- [react-native-linkedin-oauth](https://www.npmjs.com/package/react-native-linkedin-oauth)

## Licence

[MIT](https://github.com/xcarpentier/react-native-linkedin/blob/master/LICENSE)

> made with ♥
