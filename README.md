
Deployed at goerli:
1. address: 0x7F645349D81888904a146F0b52F48Ef189356D84
2. address: 0xA4434dD27255f3A21e0829792832414CDD5f9a9C

# Create new Project:

``` 
npm install --save-dev hardhat
npx hardhat
npx hardhat compile
```

<br>
<br>

For understand the SafeMoon project, 1st we should understand the uniswap, and in this repo we explain the uniswap and provide some resources for more details.

<br>
<br>


## Uniswap Introduction Part 1 
explain the followings topics [link](https://medium.com/@gregshen0925/decentralized-exchange-intro-3ab7c3937041):


- Centralized Exchange(CEX) and Decentralized Exchange(DEX)
- Market Maker
- Automated Market Maker(AMM)
- Constant Product Formula (k=x*y)
- Uniswap V2 Main Features
    - Token Swap
    - Liquidity Providing
        - Provide two tokens to mint LP token
        - Stake LP token
        - Unstake LP token
        - Burn LP token back to two tokens
    - Oracle
    - Flash Loans

<br>
<br>



### Architecture of Uniswap Smart Contracts
There are two repositories which both contains two main smart contracts:
1. Core
2. Periphery
        
### 1. Core
Core is for storing values(tokens) and managing them. It contains two smart contracts, Pair and Factory.

1. **Pair**: 
Smart contract that implements functionality for swapping, minting and burning tokens.

2. **Factory**: 
Creating and tracking pairs

### 2. Periphery
Periphery, obviously, contains smart contract to interact with Core. It also contains two smart contracts, Router and Library

1. **Router**: 
Interacting with the core. Provides functionalities such as swapETHForExactTokens, swapExactETHForTokens, etc.

2. **Library**: 
Some functionalities like getReserves, getAmountIn, getAmountOut, etc.

<br>
<br>
<br>

## Uniswap Introduction Part 2 
explain the followings topics [link](https://medium.com/coinmonks/uniswap-introduction-2-c60e66530e68):

- Pair
- Mint
- FeeOn and mintFee
- Burn
- Swap
- Swapping Fee

<br>
<br>
<br>


# SafeMoon [link](https://github.com/safemoonprotocol/Safemoon.sol/blob/main/Safemoon.sol)

SafeMoon use the betst math for the tokonomic. It's distribute the reward among all token holders 
without transfering the tokens. <br> 
SafeMoon use the `refelection` amount that will gradually decrease whenever the transaction will happen. <br>
It's does not have any `mint` and `burn` method for minting the new tokens and for burning the existing tokens. <br>
It's set their supplay 1 Quadrillion and transfer all tokens to the owner at their deployment time. <br>

But their supplay will be gradually increase because when they give the reward to their token holders they actully mint the new token by using the math that they will use for transfering/give the reward. <br>

Because thy use the `refelection` that refelection will decrease after each transaction and this `refelection` will impact on their total supplay and this the total mathematics. <br>

And user can also burn their tokens by transfering the liqudity pool. It's did't have any `burn` method but the tokens that will transfer to the `liqudity pool` they can consider as the `burn`. <br>

And after each transaction some percentage of tokens will be burn as the form of liqudity fee and some percentage of token will mint as the form of reward using the `refelection` amount. <br>

And may be: When the `refelection` amount will become 0 then no more token will be mint no reward will be transfer to the holders.


<br>
<br>
1. orignal safeMoon contract that we copy from their 
[given](https://github.com/safemoonprotocol/Safemoon.sol/blob/main/Safemoon.sol) 
github rep can find [here](./contracts/SafeMoon.sol).

2. and we also add comments and explain the safemoon contract and remove some unuse code which can found [here](./contracts/SafeMoon_with_Comments.sol).

<br>
<br>

## SafeMoof structure:
1. interface IERC20: use for erc20 tokens.
2. library SafeMath: use for safe arithmetic operation.
3. abstract contract Context:  use for get "msg.sender" and "msg.data".
4. library Address: use for collection of functions related to the address type
5. contract Ownable is Context: use for do some owner related operations (transferOwnership, onlyOwner, owner, etc).
6. interface IUniswapV2Factory: use for create liqudity pair eith "SafeMoon and WETH" 
7. interface IUniswapV2Pair: this will not use in SafeMoon but when we create new liqudity pair that pair contract will be the instance of this interface.

8. interface IUniswapV2Router01: use for use the uniswap function `addLiquidityETH`.
9. interface IUniswapV2Router02 is IUniswapV2Router01: use for the the uniswap function `swapExactTokensForETHSupportingFeeOnTransferTokens`.


10. SafeMoon is Context, IERC20, Ownable: this is the actuall safemoon contract in which implement the app "SafeMoon" tokonomic.


