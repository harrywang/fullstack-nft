# About

My note and code for tutorial at https://dev.to/dabit3/building-scalable-full-stack-apps-on-ethereum-with-polygon-2cfb

# Setup

```
npx create-next-app nft-marketplace

cd nft-marketplace

npm install ethers hardhat @nomiclabs/hardhat-waffle \
ethereum-waffle chai @nomiclabs/hardhat-ethers \
web3modal @openzeppelin/contracts ipfs-http-client \
axios dotenv

npm install -D tailwindcss@latest postcss@latest autoprefixer@latest

```

Next, we will create the configuration files needed for Tailwind to work with Next.js (tailwind.config.js and postcss.config.js) by running the following command:

```
npx tailwindcss init -p
```

update tailwind.config.js
```
/* tailwind.config.js */
module.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

update nft-marketplace/styles/globals.css

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

config hardhat:

```
npx hardhat
```

update hardhat.config.js

```
/* hardhat.config.js */
require("@nomiclabs/hardhat-waffle")

module.exports = {
  defaultNetwork: "hardhat",
  networks: {
    hardhat: {
      chainId: 1337
    },
//  unused configuration commented out for now
//  mumbai: {
//    url: "https://rpc-mumbai.maticvigil.com",
//    accounts: [process.env.privateKey]
//  }
  },
  solidity: {
    version: "0.8.4",
    settings: {
      optimizer: {
        enabled: true,
        runs: 200
      }
    }
  }
}
```

add the contract

add the test and run the test

```
npx hardhat test
```

add all frontend files

start local node:

```
npx hardhat node
```

deploy to local network:

```
npx hardhat run scripts/deploy.js --network localhost

nftMarketplace deployed to: 0x5FbDB2315678afecb367f032d93F642f64180aa3
```

config.js is also created.

import the local testing account to metamask and start node server:

```
npm run dev
```

http://localhost:3000


deploy to Mumbai:

```
npx hardhat run scripts/deploy.js --network mumbai

nftMarketplace deployed to: 0xA5a976B6950446e44B0dBc2515B4648E1DAa2014
```

https://mumbai.polygonscan.com/address/0xA5a976B6950446e44B0dBc2515B4648E1DAa2014

```
npm run dev
```
NOTE: run into an error:
<img width="960" alt="Screen Shot 2022-03-24 at 9 48 20 PM" src="https://user-images.githubusercontent.com/595772/160038880-76eeb621-4311-42b0-82c0-1ae7394c9a66.png">


to fix: go to https://mumbai.polygonscan.com/address/0xA5a976B6950446e44B0dBc2515B4648E1DAa2014 find the following address:

<img width="1197" alt="Screen Shot 2022-03-24 at 9 50 13 PM" src="https://user-images.githubusercontent.com/595772/160038932-17cf20d5-5e20-4b99-a7f2-2acd25f07937.png">

and update the address in `nft-marketplace/config.js`, then run `npm run dev` again, it should work.

deploy to polygon:

```
npx hardhat run scripts/deploy.js --network matic
nftMarketplace deployed to: 0xA5a976B6950446e44B0dBc2515B4648E1DAa2014
```

https://polygonscan.com/address/0xA5a976B6950446e44B0dBc2515B4648E1DAa2014

update 1. config.js use the correct contract address 2. index.js: https://polygon-mainnet.g.alchemy.com/v2/hPUgsSvT5Sxbx2V-uxV-2EIToiUfbD0F

