# Create new Project:

``` 
npm install --save-dev hardhat
npx hardhat
npx hardhat compile
```


# SafeMoon BAsics:
## interface IERC20:
- function totalSupply() external view returns (uint256);
- function balanceOf(address account) external view returns (uint256);
- function transfer(address recipient, uint256 amount) external returns (bool);
- function allowance(address owner, address spender) external view returns (uint256);
- function approve(address spender, uint256 amount) external returns (bool);
- function transferFrom(address sender, address recipient, uint256 amount) external returns (bool);
- event Transfer(address indexed from, address indexed to, uint256 value);
- event Approval(address indexed owner, address indexed spender, uint256 value);


## library SafeMath:
- unction add(uint256 a, uint256 b) internal pure returns (uint256)
- function sub(uint256 a, uint256 b) internal pure returns (uint256)
- function sub(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256)
- function mul(uint256 a, uint256 b) internal pure returns (uint256)
- function div(uint256 a, uint256 b) internal pure returns (uint256)
- function div(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256)
- function mod(uint256 a, uint256 b) internal pure returns (uint256)
- function mod(uint256 a, uint256 b, string memory errorMessage) internal pure returns (uint256)

## library Address:
- function isContract(address account) internal view returns (bool)
- function sendValue(address payable recipient, uint256 amount) internal
- function functionCall(address target, bytes memory data) internal returns (bytes memory)
- function functionCall(address target, bytes memory data, string memory errorMessage) internal returns (bytes memory)
- function functionCallWithValue(address target, bytes memory data, uint256 value) internal returns (bytes memory)
- function functionCallWithValue(address target, bytes memory data, uint256 value, string memory errorMessage) internal returns (bytes memory)
- function _functionCallWithValue(address target, bytes memory data, uint256 weiValue, string memory errorMessage) private returns (bytes memory)


## abstract contract Context:
- function _msgSender() internal view virtual returns (address payable)
- function _msgData() internal view virtual returns (bytes memory)


## contract Ownable is Context:
- event OwnershipTransferred(address indexed previousOwner, address indexed newOwner);
- constructor () internal
- modifier onlyOwner()
- function owner() public view returns (address)
- function renounceOwnership() public virtual onlyOwner
- function transferOwnership(address newOwner) public virtual onlyOwner
- function geUnlockTime() public view returns (uint256)
- function lock(uint256 time) public virtual onlyOwner
- function unlock() public virtual



## interface IUniswapV2Factory: 
// Use for Create a uniswap pair for this new token

- event PairCreated(address indexed token0, address indexed token1, address pair, uint);
- function feeTo() external view returns (address);
- function feeToSetter() external view returns (address);
- function getPair(address tokenA, address tokenB) external view returns (address pair);
- function allPairs(uint) external view returns (address pair);
- function allPairsLength() external view returns (uint);
- function createPair(address tokenA, address tokenB) external returns (address pair);
- function setFeeTo(address) external;
- function setFeeToSetter(address) external;


## interface IUniswapV2Pair:
// not use in SafeMoon File

- event Approval(address indexed owner, address indexed spender, uint value);
- event Transfer(address indexed from, address indexed to, uint value);
- function name() external pure returns (string memory);
- function symbol() external pure returns (string memory);
- function decimals() external pure returns (uint8);
- function totalSupply() external view returns (uint);
- function balanceOf(address owner) external view returns (uint);
- function allowance(address owner, address spender) external view returns (uint);
- function approve(address spender, uint value) external returns (bool);
- function transfer(address to, uint value) external returns (bool);
- function transferFrom(address from, address to, uint value) external returns (bool);
- function DOMAIN_SEPARATOR() external view returns (bytes32);
- function PERMIT_TYPEHASH() external pure returns (bytes32);
- function nonces(address owner) external view returns (uint);
- function permit(address owner, address spender, uint value, uint deadline, uint8 v, bytes32 r, bytes32 s) external;
- event Mint(address indexed sender, uint amount0, uint amount1);
- event Burn(address indexed sender, uint amount0, uint amount1, address indexed to);
- event Swap(address indexed sender, uint amount0In, uint amount1In, uint amount0Out, uint amount1Out, address indexed to);
- event Sync(uint112 reserve0, uint112 reserve1);
- function MINIMUM_LIQUIDITY() external pure returns (uint);
- function factory() external view returns (address);
- function token0() external view returns (address);
- function token1() external view returns (address);
- function getReserves() external view returns (uint112 reserve0, uint112 reserve1, uint32 blockTimestampLast);
- function price0CumulativeLast() external view returns (uint);
- function price1CumulativeLast() external view returns (uint);
- function kLast() external view returns (uint);
- function mint(address to) external returns (uint liquidity);
- function burn(address to) external returns (uint amount0, uint amount1);
- function swap(uint amount0Out, uint amount1Out, address to, bytes calldata data) external;
- function skim(address to) external;
- function sync() external;
- function initialize(address, address) external;



# interface IUniswapV2Router01:
// use for IUniswapV2Router02 and it's inharitanve 

- function factory() external pure returns (address);
- function WETH() external pure returns (address);
- function addLiquidity(address tokenA, address tokenB, uint amountADesired, uint amountBDesired, uint amountAMin, uint amountBMin, address to, uint deadline) external returns (uint amountA, uint amountB, uint liquidity);
- function addLiquidityETH(address token, uint amountTokenDesired, uint amountTokenMin, uint amountETHMin, address to, uint deadline) external payable returns (uint amountToken, uint amountETH, uint liquidity);
- function removeLiquidity(address tokenA, address tokenB, uint liquidity, uint amountAMin, uint amountBMin, address to, uint deadline) external returns (uint amountA, uint amountB);
- function removeLiquidityETH(address token, uint liquidity, uint amountTokenMin, uint amountETHMin, address to, uint deadline) external returns (uint amountToken, uint amountETH);
- function removeLiquidityWithPermit(address tokenA, address tokenB, uint liquidity, uint amountAMin, uint amountBMin, address to, uint deadline, bool approveMax, uint8 v, bytes32 r, bytes32 s) external returns (uint amountA, uint amountB);
- function removeLiquidityETHWithPermit(address token, uint liquidity, uint amountTokenMin, uint amountETHMin, address to, uint deadline, bool approveMax, uint8 v, bytes32 r, bytes32 s ) external returns (uint amountToken, uint amountETH);
- function swapExactTokensForTokens(uint amountIn, uint amountOutMin, address[] calldata path, address to, uint deadline) external returns (uint[] memory amounts);
- function swapTokensForExactTokens(uint amountOut, uint amountInMax, address[] calldata path, address to, uint deadline) external returns (uint[] memory amounts);
- function swapExactETHForTokens(uint amountOutMin, address[] calldata path, address to, uint deadline) external payable returns (uint[] memory amounts);
- function swapTokensForExactETH(uint amountOut, uint amountInMax, address[] calldata path, address to, uint deadline) external returns (uint[] memory amounts);
- function swapExactTokensForETH(uint amountIn, uint amountOutMin, address[] calldata path, address to, uint deadline) external returns (uint[] memory amounts);
- function swapETHForExactTokens(uint amountOut, address[] calldata path, address to, uint deadline) external payable returns (uint[] memory amounts);

- function quote(uint amountA, uint reserveA, uint reserveB) external pure returns (uint amountB);
- function getAmountOut(uint amountIn, uint reserveIn, uint reserveOut) external pure returns (uint amountOut);
- function getAmountIn(uint amountOut, uint reserveIn, uint reserveOut) external pure returns (uint amountIn);
- function getAmountsOut(uint amountIn, address[] calldata path) external view returns (uint[] memory amounts);
- function getAmountsIn(uint amountOut, address[] calldata path) external view returns (uint[] memory amounts);



// pragma solidity >=0.6.2;

## interface IUniswapV2Router02 is IUniswapV2Router01:
// use in SafeMoon Contract
// IUniswapV2Router02 public immutable uniswapV2Router;
// IUniswapV2Router02 _uniswapV2Router = IUniswapV2Router02(0x05fF2B0DB69458A0750badebc4f9e13aDd608C7F);

- function removeLiquidityETHSupportingFeeOnTransferTokens(address token, uint liquidity, uint amountTokenMin, uint amountETHMin, address to, uint deadline) external returns (uint amountETH);
- function removeLiquidityETHWithPermitSupportingFeeOnTransferTokens(address token, uint liquidity, uint amountTokenMin, uint amountETHMin, address to, uint deadline, bool approveMax, uint8 v, bytes32 r, bytes32 s) external returns (uint amountETH);
- function swapExactTokensForTokensSupportingFeeOnTransferTokens(uint amountIn, uint amountOutMin, address[] calldata path, address to, uint deadline) external;
- function swapExactETHForTokensSupportingFeeOnTransferTokens(uint amountOutMin, address[] calldata path, address to, uint deadline)external payable;
- function swapExactTokensForETHSupportingFeeOnTransferTokens(uint amountIn, uint amountOutMin, address[] calldata path, address to, uint deadline) external;



