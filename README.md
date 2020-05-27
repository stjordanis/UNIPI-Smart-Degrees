# Diploma Validation Platform 🎓
# 🔥 Ethereum and VueJS DApp 🔷

This is a simple decentralized application built using **Ethereum** blockchain and **Vue JS** for the front-end.

## Use Case:
Selected members of an institution sign degrees.

After enough signatures have been gathered for an individual, he is considered a graduate.

Anyone with this person's details can verify he is a graduate.

# Prerequisite
- NPM version 5.8.0
- TRUFFLE verson 4.1.5
- Ganache or your private network
- Metamask

### Main skeleton of the app was found [here](https://github.com/danielefavi/ethereum-vuejs-dapp)

# Installation

1) ```sh
   sudo npm install truffle -g
   git clone git@github.com:catman85/UNIPI-Smart-Degrees.git
   cd UNIPI-Smart-Degrees/
   ```
   
2) Start ganache UI for windows.

   Click the little settings icon on the top-right.
   
   Under the workspace tab add your truffle project file. **UNIPI-Smart-Degrees/truffle.js**
   
   Save and your workspace and launch it.
   
3) Open the terminal in the folder **UNIPI-Smart-Degrees/** and run the command:
```sh
truffle console --network ganache
```
4) If ganache is running you should be inside the truffle console; now run the following command in the truffle console:
```sh
> migrate --reset --compile-all
```
5) If the migration was successful, copy the file **~/UNIPI-Smart-Degrees/build/contracts/Degrees.json** (which contains the "abi") into the folder **~/UNIPI-Smart-Degrees/frontend/src/assets/**
6) Open another terminal in the folder **UNIPI-Smart-Degrees/frontend** and run the command (without sudo):
```sh
npm install
```
7) Once all the dependencies are installed run the command:
```sh
npm run serve
```
If everything went fine, the terminal will display a message similar to:
```sh
DONE  Compiled successfully in 5166ms           15:54:53

Your application is running here: http://localhost:8080
```
8) Open the browser, go to the URL shown by your terminal and play with the DApp!

**NOTE:** You can use the same seed in Ganache and Metamask for convenience.

To create more accounts (pairs of public and private keys) in MetaMask: (they all derive from the same seed.)

1) Click the favicon (your account image) on the top right of your MetaMask pop up
2) Click “Create Account”
3) A new MetaMask account is created
4) Click “edit” above the account name to change it.
5) Make sure the newly created account is matching the account generated by ganache (have a look in ganache's Account tab).


# To interact with the contract using truffle
1) Replace the addresses in the constructor from the contracts/Degrees.sol file, with your own.
~~~
constructor() public {
    owner = msg.sender;
    addProf(address(0x4B0897b051...),"mf");
    addProf(address(0x583031D111...),"kanatas");
    ...
}
~~~
    OR use this seed: "save lyrics plate shrimp warm credit december salon velvet announce outer hamster"

2) fire up your ganache workspace and then from the project directory run,

```sh
truffle console --network ganache
>migrate --reset --compile-all
>let instance = await Degrees.deployed()
>let accounts = await web3.eth.getAccounts()
>accounts
>instance.professors
>instance.getProfessorIndex({from: accounts[0]})
>instance.signGraduation("a",{from: accounts[0]})
>instance.verifyGraduation("a") 
>instance.signGraduation("a",{from: accounts[1]})
>instance.verifyGraduation("a")
```

# To run tests
fire up ganache and then,

```sh
truffle console --network ganache
> test --reset-all
```
# Using the same Accounts in multiple Workstations
It is very convenient to share the same accounts in Ganache/MetaMask from multiple development workstations. To achieve this you need to:

0) Generate a new seed with metamask. Once you have that seed,
1) Create a new workspace with Ganache:
2) Under Accounts&Keys enter the menomonic you generated with MetaMask.
3) Under Workspace add the **UNIPI-Smart-Degrees/truffle.js** project file.
4) Save your Workspace and launch it.
5) finally run ``` truffle console --network ganache ``` and you should be inside the truffle console.
6) When developing from a new machine, follow the same steps from 1.


**NOTE** the /frontend/build/ directory is needed for ``` npm install && npm run serve```

# Connecting MetaMask with Ganache
0) Open the MetaMask addon and find where it says **Main Ethereum Network**
1) Click that and select **Custom RPC**
2) Give your test net a name and now for the important part.
3) Look at the Ganache GUI, there should be a **RPC Server** indication.
4) Copy and paste that url to the MetaMask field and refresh your frontend.
5) Boom, you are connected!

# Development Quickstart (Linux & Mac)
Open Ganache UI

Make sure you have installed expect and xterm in your machine.
```sh
apt-get install expect xterm
```
Make sure the **start.sh** script has execution privilages.
```sh
chmod +x start.h
```

After opening the Ganache GUI, open yout browser, sign in to MetaMask and connnect to Ganache's RPC network.

Then execute:
```sh
./start.sh
```

This little script will :
- connect truffle with ganache
- test your contracts
- copy the compiled contracts
- run the frontend part of the app

# Development Quickstart (Windows WSL)
Open Ganache UI.

Make sure you have installed expect in your machine. And you are located in the project's root directory
```sh
apt-get install expect
```
After opening up Ganache UI,

run: 
```sh
expect trufflexp.exp
```
After the first command is done, in another terminal:
```sh
cp build/contracts/Degrees.json frontend/src/assets/Degrees.json
```

Then open your browser, sign in to MetaMask and connect to Ganache's RPC network.

Finally, in another terminal:
```sh
cd frontend/ && npm run serve
```

# Screenshots

![ ](https://i.imgur.com/glHe5Jc.jpg "")

![ ](https://i.imgur.com/6PfVymV.jpg "")

![ ](https://i.imgur.com/yKsbl11.jpg "")

![ ](https://i.imgur.com/w0vzWzI.jpg "")

![ ](https://i.imgur.com/oj7JYdz.jpg "")

![ ](https://i.imgur.com/elaT4tR.jpg "")

![ ](https://i.imgur.com/efhThA4.jpg "")
