# hardhat_learning
hardhat初步学习
学习地址:[https://hardhat.org/tutorial]

1. 环境配置
   MacOS somma 14.4.1 (23E224)
  ```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
nvm install 20
nvm use 20
nvm alias default 20
npm install npm --global # Upgrade npm to the latest version
  ```
2. 创建HardHat项目
  ```
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
```
cd contracts
npx hardhat compile
```
4. 测试合同
```
cd test
npx hardhat test
```
5. 调试 HardHat NetWork
```
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
   ```
   npx hardhat ignition deploy ./ignition/modules/Token.js --network <network-name>
   # 我这里用的是Sepolia, 以太坊API有Infura和Alchemy，我用的是Infura
   ```
7. 样板项目
   
