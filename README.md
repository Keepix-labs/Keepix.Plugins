# Keepix.Plugins

## list.json

The file list.json is automatically loaded by the keepix-server each 10 minutes.  
This file contains an array who contains each plugins definitions.  

## Define a new Plugin
  
Fork the repository and define your plugin on like this example:  
When your json of plugin representation is ready please create a new pull request on the main branch target.  
  
```js
{
  "id": "pluginId", // equals to the name of your plugin binary
  "repositoryUrl": "...", // url of the plugin source code github repository
  "packageName": "keepix-plugin-smart-node-build", // name of the npmjs package published
  "title": "Ninja Plugin", // title displayed on the Keepix for your plugin
  "description": "blabla...blabla...", // Description of what your plugin do and each important information before downloading it
  "icon": "cryptocurrency:eth", // icon for your plugin ref: https://icon-sets.iconify.design/
  "platforms": ["linux-arm64", "linux-x64", "win-x64", "win-arm64", "oxs-x64", "oxs-arm64"], // supported platforms for your plugin (represent the bin/linux-arm64,bin/linux-64,... present on your final build directory)
  "requires": { // requirement section
     "ports": [
       {
         "internal": 30303, // internal port exposed by the computer where the plugin are running on
         "external": 30303, // external port exposed by the ethernet box
         "protocol": "TCP", // TCP or UDP
         "description": "keepix-upnp-nethermind-tcp" // description for the user
       },
       ...
     ],
     "installForm": {
       "inputs": [
         { // example of get Mnemonic of one wallet at the install step
             "key": "WalletMnemonic",
             "type": "wallet",
             "walletType": "ethereum",
             "walletKey": "mnemonic",
             "filter": "wallet.asMnemonic === true",
             "label": "Select a Ethereum Wallet.",
             "labelIfEmptyWalletList": "Please go on wallets page and create or import (with mnemomic) an Ethereum Wallet."
         },
         { // example of a checkbox-2
             "key": "AutoStart",
             "type": "checkbox-2",
             "true": "Yes",
             "false": "No",
             "defaultValue": true,
             "label": "Auto Start"
          },
          ... // more input will be available in the future (Ask the team if you need a specifical input).
       ],
       "description": "Please select fill the form before install the plugin." // description for the install form
     }
  }
}
```
