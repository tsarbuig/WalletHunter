![image](https://user-images.githubusercontent.com/70858574/190273360-85035735-dd90-45a7-bb9a-d48a9c7064ed.png)

ℹ️ Visit my website : https://wallethunter.app/

📖 Check all new features in [Releases page](https://github.com/tsarbuig/WalletHunter/releases)

&nbsp;

WalletHunter is the only copytrading bot available on the market. Find profitables wallets, and...
- they buy  --> you buy 
- they sell --> you sell

and even better... you frontrun the original Tx :)

&nbsp;

# How does it works?
1/ Find some profitable wallets

2/ Enter them into the bot

3/ Define your strategy :
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

# Who am I?
I’m the lead dev of LimitSwap, one of the first Crypto Trading bot launched on the market.
(even though this bot was originally created by @CryptoGnome, my Coding Master :) )

LimitSwap is still my #1 project with more than 500 users, along with Sniper Bot, also one of the first Sniping Bot available.

Feel free to join our community:  https://t.me/LimitSwap 


&nbsp;

# How can I buy it?
Contact @TsarBuig on Telegram

![image](https://user-images.githubusercontent.com/70858574/186655675-dc18f57a-868b-4eab-9460-22efa9feccc9.png)

&nbsp;

# Bot configuration

#### BUY/SELL amounts
```yaml
WALLETHUNTER_MODE: "buy_and_autosell", 
// WALLETHUNTER_MODE available values : 
- buy_and_sell --> will copy all buy/sell Tx from wallet
- buy_and_autosell --> will copy buy Tx but will sell automatically after xx% of profit. Target is defined by AUTOSELL_PROFIT parameter
- buy_only --> will only copy buys

BUY_AMOUNT: "10%", 
// BUY_AMOUNT available values : 
- "xx%" --> Example : with '50%', if tracked wallet buys 1 BNB, you will buy 0.5 BNB
- "same_as_tx" --> use same value than the wallet you hunt

SELL_AMOUNT: "100%", 
// SELL_AMOUNT available values : 
- "xx%" --> it will sell  xx%  of the amount of those tokens that you hold in your wallet
- "same_as_tx" --> use same value than the wallet you hunt
- "same_strategy" --> will copy your hunted wallet's sell strategy : if hunted wallet sells 10% of his bag, you will sell 10% of your bag too

AUTOSELL_PROFIT: "200%", // if you use 'buy_and_autosell' mode, bot will automatically sell token when price has reached buyprice * AUTOSELL_PROFIT

// MULTIBUY
AMOUNT_OF_BUYS: 1, // increment number if you want the bot to make multiple buys in the same block

```

#### Wallets that you want to hunt
```yaml
TRACKED_WALLET : ["0x57825dd07df69d2d3bc800356133562770e7f0a1", "0x842550340af19d6e1af4cc1083a25e9c83c26f05"],
```

#### Track all tokens or not ?
```yaml
ONLY_TRACK_SPECIFIC_TOKENS : false,
TRACKED_TOKENS : ["0x0E09FaBB73Bd3Ade0a17ECC321fD13a19e81cE82", "0x42981d0bfbAf196529376EE702F2a9Eb9092fcB5"],
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
Tx_GAS_FOR_BUY : '100%', // GAS used for BUY Tx
Tx_GAS_FOR_SELL: '120%', // same as above but for SELL Tx
// Tx_GAS_FOR_xxx available values : 
- "xx%" --> example : with '120%', if tracked wallet uses GAS = 10, you will use GAS = 12
- "same_as_tx" --> use same value than the wallet you hunt
- "BOOST" --> bot will check Current Market GAS value, then apply a % of raise defined by GAS_BOOST parameter.

GAS_BOOST: '40%', // check above
GASPRIORITY_FOR_ETH_ONLY : 2 // for EIP1559 Tx
```

#### When stop the bot
```yaml
AMOUNT_OF_BUY_TX_BEFORE_THE_BOT_STOP : 2, // bot will stop automatically after this amount of BUY Tx made in a row
STOP_IF_BALANCE_IS_LOWER_THAN : 0.02, // bot will stop automatically if balance goes under this amount (to avoid being scammed by honeypot)
```

#### Antirug
```yaml
ACTIVATE_ANTIRUG : true, // use it if the wallet you track does not have its own antirug protection
LIQUIDITY_REMOVAL_PERCENTAGE : 0.0001, // Force sell all your tokens is liquidity removal > LIQUIDITY_REMOVAL_PERCENTAGE
GAS_MULTIPLIER : 2.0, // in case of force sell after detecting a rug, multiply original Tx Gas by GAS_MULTIPLIER
```

# Dedicated modes

#### FORCESELL mode
```yaml
./WalletHunter --forcesell  : use this mode if you want to sell all your tokens in 1 click
```

#### AUTOSELL mode
```yaml
./WalletHunter --autosell  : use this mode if you want he bot to sell all your tokens after a xx% profit 
```

#### ANTIRUG mode
```yaml
./WalletHunter --antirug  : use this mode if you want to start antirug mode on a token you already hold
```
