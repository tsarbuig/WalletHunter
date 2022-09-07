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

https://user-images.githubusercontent.com/70858574/186656960-d5b8152a-26d4-46e0-9f37-2d9deb12ffb4.mp4


&nbsp;

# Things you need to know
1/ You need a private or semi private node to make it work (because it scans mempool)

2/ As you may know, there are lots and lots of ways to make swaps, and I need to implement them into WalletHunter.
Don't worry, all the usual ways are implemented, but when you find a wallet that you want to copy, send it to me (if it's ok for you) , and I'll tell you if WalletHunter is able to copy it

3/ Only big limitation known today : UniswapV3 Tx are not clonable for now --> I'm working on it

&nbsp;

# How can I buy it?
Contact @TsarBuig on Telegram

![image](https://user-images.githubusercontent.com/70858574/186655675-dc18f57a-868b-4eab-9460-22efa9feccc9.png)

&nbsp;

# Bot configuration

#### BUY/SELL amounts
```yaml
BUY_AMOUNT: "10%", // you can use percentage here. Example : with "50%"", if tracked wallet buys 1 BNB, you will buy 0.5 BNB
SELL_AMOUNT: "100%", // if you copy a SELL Tx, it will sell  xx%  of the amount of those tokens that you hold in your wallet. You can also enter "same_as_tx" to use same value than the wallet you hunt
```

#### Wallets that you want to hunt
```yaml
TRACKED_WALLET : ["0x57825dd07df69d2d3bc800356133562770e7f0a1", "0x842550340af19d6e1af4cc1083a25e9c83c26f05"],
```

#### BUY protections
```yaml
TOKENS_BLACKLIST : ["0x702de1f526ac996bcfdb6512bafbe04bf619fad6", "0xe9e7cea3dedca5984780bafc599bd69add087d56", "0x55d398326f99059ff775485246999027b3197955", "0x8ac76a51cc950d9822d68b83fe1ad97b32cd580d"], // Tokens you don't want to buy. It's a list : you can enter several tokens that you don't want to trade
BUYAFTER_XXX_SECONDS : 0, 
HONEYPOT_CHECK : false, 
BUY_SEVERAL_TIME_SAME_TOKEN : true, // If "false", bot not buy anymore the token if you've already bought it before
ONLY_1_BUY_PER_BLOCK : true, // If "true", bot won't make more than 1 Tx per block. Set it to "false" if you want to track super-fast wallets with more than 1 Tx per block 
MINIMUM_BUY_AMOUNT_IN_BASE: 0.0000001, // bot won't buy if your Tx value is INFERIOR to this value (in ETH, BNB...)
MAXIMUM_BUY_AMOUNT_IN_BASE: 10, // bot won't buy if your Tx value is SUPERIOR to this value (in ETH, BNB...)
```

#### GAS  
```yaml
Tx_GAS : 120% // you can use percentage here. Example : with "120%"", if tracked wallet uses GAS = 10, you will use GAS = 12
GAS_BOOST : 10 // if you use txGas = BOOST
GAS_LIMIT : 1000000
GASPRIORITY_FOR_ETH_ONLY : 2 // for EIP1559 Tx
```

#### When stop the bot
```yaml
AMOUNT_OF_BUY_TX_BEFORE_THE_BOT_STOP : 2, // bot will stop automatically after this amount of BUY Tx made in a row
STOP_IF_BALANCE_IS_LOWER_THAN : 0.02, // bot will stop automatically if balance goes under this amount (to avoid being scammed by honeypot)
```
