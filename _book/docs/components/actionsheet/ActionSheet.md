## actionsheet-def-headref
## ActionSheet

NativeBase ActionSheet is a wrapper around the React Native [ActionSheetIOS](http://facebook.github.io/react-native/releases/0.44/docs/actionsheetios.html) component.

For `ActionSheet` to work, you need to wrap your topmost component inside `<Root>` from native-base.

{% codetabs name="React Native", type="js" -%}
import { Root } from "native-base";
import { StackNavigator } from "react-navigation";
const AppNavigator = StackNavigator(
  {
    Page: { screen: Page },
  }
);
export default () =>
  <Root>
    <AppNavigator />
  </Root>;
{%- language name="Vue Native", type="vue" -%}
<template>
  <root>
    <app-navigation></app-navigation>
  </root>
</template>
<script>
import { Root } from "native-base";
import { StackNavigator } from "vue-native-router";
const AppNavigation = StackNavigator(
  {
    Page: { screen: Page },
  }
);
export default {
  components: { Root, AppNavigation }
};
</script>
{%- endcodetabs %}


![Preview ios actionsheet-def-headref](https://github.com/GeekyAnts/NativeBase-KitchenSink/raw/v2.6.1/screenshots/ios/actionsheet.gif)
![Preview android actionsheet-def-headref](https://github.com/GeekyAnts/NativeBase-KitchenSink/raw/v2.6.1/screenshots/android/actionsheet.gif)

*General Syntax*

{% codetabs name="React Native", type="js" -%}
import React, { Component } from "react";
import { Container, Header, Button, Content, ActionSheet, Text } from "native-base";
var BUTTONS = ["Option 0", "Option 1", "Option 2", "Delete", "Cancel"];
var DESTRUCTIVE_INDEX = 3;
var CANCEL_INDEX = 4;
export default class ActionSheetExample extends Component {
  constructor(props) {
    super(props);
    this.state = {};
  }
  render() {
    return (
      <Container>
        <Header />
        <Content padder>
          <Button
            onPress={() =>
            ActionSheet.show(
              {
                options: BUTTONS,
                cancelButtonIndex: CANCEL_INDEX,
                destructiveButtonIndex: DESTRUCTIVE_INDEX,
                title: "Testing ActionSheet"
              },
              buttonIndex => {
                this.setState({ clicked: BUTTONS[buttonIndex] });
              }
            )}
          >
            <Text>Actionsheet</Text>
          </Button>
        </Content>
      </Container>
    );
  }
}
{%- language name="Vue Native", type="vue" -%}
<template>
  <nb-container>
    <nb-header/>
    <nb-content padder>
      <nb-button :onPress="handleBtnPress">
        <nb-text>Actionsheet</nb-text>
      </nb-button>
    </nb-content>
  </nb-container>
</template>

<script>
import { ActionSheet } from "native-base";
export default {
  data: function() {
    return {
      btnOptions: ["Option 0", "Option 1", "Option 2", "Delete", "Cancel"],
      optionCancelIndex: 4,
      optionDestructiveIndex: 3,
      clicked: 0
    };
  },
  methods: {
    handleBtnPress: function() {
      ActionSheet.show(
        {
          options: this.btnOptions,
          cancelButtonIndex: this.optionCancelIndex,
          destructiveButtonIndex: this.optionDestructiveIndex,
          title: "Select An Option"
        },
        buttonIndex => {
          this.clicked = this.btnOptions[buttonIndex];
        }
      );
    }
  }
};
</script>
{%- endcodetabs %}
<br />
