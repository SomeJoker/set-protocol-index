
### 使用hardhat 提供的测试账户进行 settoken的部署

## 安全帽使用
1. 初始化项目
npm init --yes
npm install  hardhat
2. 编译
npx hardhat complie
3. 启动本地测试网
npx hardhat node
4. 部署测试
npx hardhat run scripts/deploy.js 

在remix上部署应用需要花费gas,hardhat提供了20个测试账户每个账户里有10000个ETH.
然后还需要配置一下钱包的连接，自定义一个网络，地址是http://127.0.0.1:8545,还需要注意的是chainId,hardhat默认的是31337，可以通过修改hardhat.config.js中的chainId字段来修改成其他的端口


### hardhat的初始的测试账户，每台机器上可能不一样
Accounts  
Account #0: 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266 (10000 ETH)
Private Key: 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80

Account #1: 0x70997970c51812dc3a010c7d01b50e0d17dc79c8 (10000 ETH)
Private Key: 0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d

Account #2: 0x3c44cdddb6a900fa2b585dd299e03d12fa4293bc (10000 ETH)
Private Key: 0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a

Account #3: 0x90f79bf6eb2c4f870365e785982e1f101e93b906 (10000 ETH)
Private Key: 0x7c852118294e51e653712a81e05800f419141751be58f605c371e15141b007a6

Account #4: 0x15d34aaf54267db7d7c367839aaf71a00a2c6a65 (10000 ETH)
Private Key: 0x47e179ec197488593b187f80a00eb0da91f1b9d0b13f8733639f19c30a34926a

Account #5: 0x9965507d1a55bcc2695c58ba16fb37d819b0a4dc (10000 ETH)
Private Key: 0x8b3a350cf5c34c9194ca85829a2df0ec3153be0318b5e2d3348e872092edffba

Account #6: 0x976ea74026e726554db657fa54763abd0c3a0aa9 (10000 ETH)
Private Key: 0x92db14e403b83dfe3df233f83dfa3a0d7096f21ca9b0d6d6b8d88b2b4ec1564e

Account #7: 0x14dc79964da2c08b23698b3d3cc7ca32193d9955 (10000 ETH)
Private Key: 0x4bbbf85ce3377467afe5d46f804f221813b2bb87f24d81f60f1fcdbf7cbf4356

Account #8: 0x23618e81e3f5cdf7f54c3d65f7fbc0abf5b21e8f (10000 ETH)
Private Key: 0xdbda1821b80551c9d65939329250298aa3472ba22feea921c0cf5d620ea67b97

Account #9: 0xa0ee7a142d267c1f36714e4a8f75612f20a79720 (10000 ETH)
Private Key: 0x2a871d0798f97d79848a013d4936a73bf4cc922c825d33c1cf7073dff6d409c6

Account #10: 0xbcd4042de499d14e55001ccbb24a551f3b954096 (10000 ETH)
Private Key: 0xf214f2b2cd398c806f84e317254e0f0b801d0643303237d97a22a48e01628897

Account #11: 0x71be63f3384f5fb98995898a86b02fb2426c5788 (10000 ETH)
Private Key: 0x701b615bbdfb9de65240bc28bd21bbc0d996645a3dd57e7b12bc2bdf6f192c82

Account #12: 0xfabb0ac9d68b0b445fb7357272ff202c5651694a (10000 ETH)
Private Key: 0xa267530f49f8280200edf313ee7af6b827f2a8bce2897751d06a843f644967b1

Account #13: 0x1cbd3b2770909d4e10f157cabc84c7264073c9ec (10000 ETH)
Private Key: 0x47c99abed3324a2707c28affff1267e45918ec8c3f20b8aa892e8b065d2942dd

Account #14: 0xdf3e18d64bc6a983f673ab319ccae4f1a57c7097 (10000 ETH)
Private Key: 0xc526ee95bf44d8fc405a158bb884d9d1238d99f0612e9f33d006bb0789009aaa

Account #15: 0xcd3b766ccdd6ae721141f452c550ca635964ce71 (10000 ETH)
Private Key: 0x8166f546bab6da521a8369cab06c5d2b9e46670292d85c875ee9ec20e84ffb61

Account #16: 0x2546bcd3c84621e976d8185a91a922ae77ecec30 (10000 ETH)
Private Key: 0xea6c44ac03bff858b476bba40716402b03e41b8e97e276d1baec7c37d42484a0

Account #17: 0xbda5747bfd65f08deb54cb465eb87d40e51b197e (10000 ETH)
Private Key: 0x689af8efa8c651a91ad287602527f3af2fe9f6501a7ac4b061667b5a93e037fd

Account #18: 0xdd2fd4581271e230360230f9337d5c0430bf44c0 (10000 ETH)
Private Key: 0xde9be858da4a475276426320d5e9262ecfc3ba460bfac56360bfa6c4c28b4ee0

Account #19: 0x8626f6940e2eb28930efb4cef49b2d1f2c9c1199 (10000 ETH)
Private Key: 0xdf57089febbacf7ba0bc227dafbffa9fc08a93fdc68e1e42411a14efcf23656e


先部署controller,再部署creator(需要controller的地址作为参数)
还需要部署module,这里先部署一个TradeModule,TradeModule部署需要controller作为参数

然后再部署set-protocol的合约到hardhat
先部署controller
再部署module,creator
调用creator的方法创建一个DPItoken

controller
0x9fE46736679d2D9a65F0992F2272dE9f3c7fa6e0
tradeModule
0xCf7Ed3AccA5a467e9e704C703E8D87F634fB0Fc9
creator
0xDc64a140Aa3E981100a9becA4E685f962f0cF6C9



## set protocol 涉及的合约地址
### controller
主网源码地址: https://etherscan.io/address/0xa4c8d221d8bb851f83aadd0223a8900a6921a349#code
Rikeby测试网部署地址: 0x75f6C7116D84F6a872083b2005984a8B8dDAb9e8

### Trade Module
主网源码地址: https://etherscan.io/address/0x90f765f63e7dc5ae97d6c576bf693fb6af41c129#code
Rikeby测试网部署地址: 0xA9f5386a5b1b59E7456C6e8F7180d6d6A8eD4Df1

### Set Token Creator
主网源码地址: https://etherscan.io/address/0x8cb9e7bdd78926933fc9d19f5f69fefc2b737087#code
Rikeby测试网部署地址: 0xC9770e2cB5C51f493CDC3d3664f025A5725E0C92

### DPI/SetToken 
主网源码地址: https://etherscan.io/address/0x1494ca1f11d487c2bbe4543e90080aeba4ba3c2b#code
Rikeby测试网部署地址: 0x9a4c5215e67fd0b0c9e590139ed1c8612fadb8c7

### core
https://etherscan.io/address/0xf55186cc537e7067ea616f2aae007b4427a120c8#code


### Set Token Factory
https://etherscan.io/address/0xe1cd722575801fe92eeef2ca23396557f7e3b967#code

### Set Valuer
https://etherscan.io/address/0xddf4f0775ff69c73619a4dbb42ba61b0ac1f555f#code


### Transfer Proxy
0x882d80d3a191859d64477eb78cca46599307ec1c

### Vault
0x5b67871c3a857de81a1ca0f9f7945e5670d986dc

### Wrap Module
0xbe4aede1694aff7f1827229870f6cf3d9e7a999c

### Uniswap Governance Adapter
0x1f4ed52724f6f936fbb367b2388733a88d7b0f67

### Uniswap Pool Price Adapter
0xa472a8a7b21061a8839837ba342e1520a1fa63ed

###  Exchange Issuance Module V2
https://etherscan.io/address/0x8f2d580c3cccd96c3541386daac0af71c5d1c0f9#code

###  Fart Set
https://etherscan.io/address/0xffee21b4bb7084a9416205544101ae9f472c7159#code

###  Governance Module
https://etherscan.io/address/0x5c87b042494cdceba44c541fbb3bc8bff179d500#code

### Master Price Oracle
https://etherscan.io/address/0xa60f9e1641747762ade7fd5f881b90b691e92b0a#code

### Protocol Viewer
https://etherscan.io/address/0x6b65c4760f56ea89a21193af5b909395766ef2e5#code
	
### Rebalance Auction Module
https://etherscan.io/address/0xe23fb31dd2edacebf7d92720358bb92445f47fdb#code
