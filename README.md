# react-navigation-backhandler

Easily handle Android back button behavior with React-Navigation.

### Usage

The following snippet demonstrates the usage. Note that `onBackButtonPressAndroid` will only be called if `SomeComponent` is placed in a screen that is focused (the one user is directly interacting with). Behind the scenes, the `onBackButtonPressAndroid` handler is registered after entering a screen, and unregistered before going away from it, leaving you with a declarative interface to interact with.

You may use `AndroidBackHandler` component anywhere in your app's React tree, it does not need to be placed directly in the screen component.

```js
import { AndroidBackHandler } from 'react-navigation-backhandler';

class SomeComponent extends React.Component {
  onBackButtonPressAndroid = () => {
    /*
    *   Returning `true` from `onBackButtonPressAndroid` denotes that we have handled the event,
    *   and react-navigation's lister will not get called, thus not popping the screen.
    *
    *   Returning `false` will cause the event to bubble up and react-navigation's listener will pop the screen.
    * */

    if (youWantToHandleTheBackButtonPress) {
      // do something
      return true;
    } else {
      return false;
    }
  };

  render() {
    return (
      <AndroidBackHandler onBackPress={this.onBackButtonPressAndroid}>
        <BodyOfYourScreen />
      </AndroidBackHandler>
    );
  }
```
