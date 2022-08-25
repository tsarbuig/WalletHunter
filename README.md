![image](https://user-images.githubusercontent.com/70858574/186650034-07175829-a345-4920-b517-bfe7c7a72cb3.png)

WalletHunter is the only copytrading bot available on the market. Find profitables wallets, and...
- they buy  --> you buy 
- they sell --> you sell

and even better... you frontrun the original Tx :)

&nbsp;

# How does it works?
1/ Find some profitable wallets

2/ Enter them into the bot

3/ Define your parameters :
- Amount (same amount / fraction of original amount...)
- GAS
- HoneyPot check before buy
- etc.

4/ Run the bot
and... that's it !

&nbsp;

# Things you need to know
1/ You need a private or semi private node to make it work (because it scans mempool)

2/ As you may know, there are lots and lots of ways to make swaps, and I need to implement them into WalletHunter.
Don't worry, all the usual ways are implemented, but when you find a wallet that you want to copy, send it to me (if it's ok for you) , and I'll tell you if WalletHunter is able to copy it

3/ Only big limitation known today : UniswapV3 Tx are not clonable for now --> I'm working on it

&nbsp;

# Bot configuration
## Secret parameters
Open Secret_parameters.json file in the root directory of the bot. 

```
{
  "CUSTOM_NODE_WSS": "enter here your node ws address",
  "YOUR_WALLET_ADDRESS": "",
  "PRIVATE_KEY": "",
  "WALLETHUNTER_TOKEN_WALLET_ADDRESS": "",
  "WALLETHUNTER_TOKEN_WALLET_PRIVATE_KEY": ""
}
```

- YOUR_WALLET_ADDRESS - public address of your account (wallet); this address is used to buy tokens
- PRIVATE_KEY - private key of your account (wallet); key is used to sign and send buy transaction : never share this key with anyone!!!
- WALLETHUNTER_TOKEN_WALLET_ADDRESS - this bot works if you hold some special tokens --> enter here the wallet where you hold them
- WALLETHUNTER_TOKEN_WALLET_PRIVATE_KEY - private key of the wallet where you hold WalletHunter tokens

