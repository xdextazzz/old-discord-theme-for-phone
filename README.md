## Как вернуть старую тему?

1. Переходим на https://discord.com/app
2. Прожимаем комбинацию клавиш `Ctrl + Shift + I`
3. Переходим во вкладку `Console`
4. В консоль вставляем этот код:

```js
let wpRequire;
window.webpackChunkdiscord_app.push([[ Math.random() ], {}, (req) => { wpRequire = req; }]);

let UserSettingsActions = Object.values(wpRequire.c).find(x => x?.exports?.PreloadedUserSettingsActionCreators).exports;
let ProtobufTypes = Object.values(wpRequire.c).find(x => x?.exports?.BoolValue).exports;

UserSettingsActions.PreloadedUserSettingsActionCreators.updateAsync("appearance", data => {
    data.mobileRedesignDisabled = ProtobufTypes.BoolValue.create({value: true})
}, UserSettingsActions.UserSettingsDelay.INFREQUENT_USER_ACTION)
```

### Код изменять не надо!

PS. Это лишь временное решение. Discord начнет игнорировать этот параметр в одном из будущих обновлений.
