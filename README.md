# hardhat_learning
hardhat初步学习
学习地址:[https://hardhat.org/tutorial]

1. 环境配置
   MacOS somma 14.4.1 (23E224)
  ```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
nvm install 20
nvm use 20
nvm alias default 20
npm install npm --global # Upgrade npm to the latest version
  ```
2. 创建HardHat项目
  ```sh
cd hardhat-tutorial
npm init
# 安装hardhat
npm install --save-dev hardhat
npx hardhat init
选择 Create an empty hardhat.config.js
# 安装推荐插件
npm install --save-dev @nomicfoundation/hardhat-toolbox
添加第一行到hardhat.config.js
-> require("@nomicfoundation/hardhat-toolbox");

/** @type import('hardhat/config').HardhatUserConfig */
module.exports = {
  solidity: "0.8.24",
};
  ```
3. 编写和编译合同
```sh
cd contracts
npx hardhat compile
```
4. 测试合同
```sh
cd test
npx hardhat test
```
5. 调试 HardHat NetWork
```sh
# 在Token.sol中添加
import "hardhat/console.sol";
# 添加到function transfer
   console.log(
        "Transferring from %s to %s %s tokens",
        msg.sender,
        to,
        amount
   );
```
6. 部署-实时网络
   ```sh
   npx hardhat ignition deploy ./ignition/modules/Token.js --network <network-name>
   # 我这里用的是Sepolia, 以太坊API有Infura和Alchemy，我用的是Infura
   ```
7. 样板项目
   - 克隆存储库[https://github.com/NomicFoundation/hardhat-boilerplate]
   ```sh
   git clone https://github.com/NomicFoundation/hardhat-boilerplate.git
   cd hardhat-boilerplate
   npm install
   npx hardhat node
   ```
   连接钱包实例
   
   ```sh
   npx hardhat run scripts/deploy.js --network localhost
   ```
   注: 上述命令报错 Transaction reverted and Hardhat couldn't infer the reason. UNPREDICTABLE_GAS_LIMIT；

   解决方案：Solidity0.8.24不兼容，必须采用原生0.8.17
   
   启动Web应用程序
   ```sh
   cd frontend
   npm install
   npm run start
   ```
   Open http://localhost:3000/
   
   连接MetaMask账户（Coinbase账户也行），切换到测试网络localhost 8545
   
   输入faucet命令获取100MHT（chain ID:0x7a69,GO）和1ETH
   ```sh
   npx hardhat --network localhost faucet <your address>
   ```
   向其他账户发送MHT
   <img width="360" alt="image" src="https://github.com/Illusionist0/hardhat_learning/assets/45280235/897033b9-07b9-44d2-ada4-1f1dbae13cf5">

   <img width="1148" alt="image" src="https://github.com/Illusionist0/hardhat_learning/assets/45280235/5e91b8b2-a687-47c0-ba3c-0313bc8e1dc0">

   <img width="838" alt="image" src="https://github.com/Illusionist0/hardhat_learning/assets/45280235/7704cd5d-b097-456f-99c9-e6c01df9866b">

   <img width="809" alt="image" src="https://github.com/Illusionist0/hardhat_learning/assets/45280235/aa101070-ee5c-4ecd-a557-ab7931b14e05">

