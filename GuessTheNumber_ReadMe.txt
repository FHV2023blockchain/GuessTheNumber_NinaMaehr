----------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Introduction:**

Welcome to GuessTheNumber!

In this game, it is your goal to correctly guess a number, which gets randomized at the start of each game session.
The number is inside the range of 0 - 30!
For this smart contract, you have two methods at your disposal:
    -> startGame(): Lets you start the game, through which the random number gets generated.
    -> checkNumber(int): Make your guess with any int number. 

For startGame(), you have to pay Sepolia ETH. An amount > (higher than) 0.01 Sepolia ETH has to be paid to be able to start the game.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Before you start:**

To set up everything for the GuessTheNumber game, you first have to follow the following steps:
    0. Install Truffle (via npm).
    1. Create a folder for your project and use the command truffle init to create a truffle directory.
    2. Add your own config.json file inside your project and enter your MNEMONIC phrase and INFURA_API_KEY.
    3. Change your setting inside the file truffle-config.js correctly (like it was done in class -> look up In-Class Task 2 and 3 as reference).
    4. Download the zipped build folder for GuessTheNumber from the GitHub Repository.
    5. Paste the unzipped build folder (which contains the Abi file for GuessTheNumber (GuessTheNumber.json) inside) into your project.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
**How to start the game:**

!Remember: The contract address for this smart contract on the Sepolia network is: 0x1774B08faA52a29221067320E845c1CcF7C2b048

To start the GuessTheNumber contract game, open the truffle console in the command line inside your project folder (truffle console --network sepolia).
After that, enter the following: (Words in CAPS need to be entered by yourself)

const abi = require("./build/contracts/GuessTheNumber.json");
var game = new web3.eth.Contract(abi['abi'],"0x1774B08faA52a29221067320E845c1CcF7C2b048")

After that, you can play the GuessTheNumber game inside your command line!

To (re)start the game (with additional fees), enter into the command line:
game.methods.startGame().send({from: 'YOUR_OWN_PUBLIC_ADDRESS', value: web3.utils.toWei("VALUE")}) (example for VALUE could be "0.011")

Through this, a new random number between 0 and 30 gets generated.

To give a guess on what the random number could be, enter into the command line:
game.methods.checkNumber(RANDOM_INT).call() (example for RANDOM_INT could be 15)

When getting the correct number, you can start the game anew by calling startGame() again!