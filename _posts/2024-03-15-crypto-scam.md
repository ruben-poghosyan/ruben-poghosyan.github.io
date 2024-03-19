---
title: "Unveiling the Rise of Cryptocurrency Scams: How AI and Deceptive Tactics Target Tech-Savvy Individuals"
categories:
  - blog
tags:
  - crypto
  - hacking
---


It's a well-known fact that scammers frequently prey on older individuals who may have limited computer literacy, crafting intricate schemes and employing various tactics to carry out their fraudulent activities. Nonetheless, recent trends, coupled with my own observations, indicate a notable increase in cryptocurrency scams, which seemingly target individuals with a higher level of computer proficiency. 

Many scams nowadays are incorporating AI elements to enhance their schemes. For instance, some scammers purchase YouTube channels with large subscriber bases, often naming them after popular AI-related channels like OpenAI. To add credibility, they may initiate live stream videos featuring original content alongside an active chat, where they promote "crypto doubling schemes". Alternatively, they produce tutorials on "crypto trading with bots", garnishing them with high view counts, likes, and positive comments. Coupled with the current technological advancements and the cryptocurrency trends, these tactics can lure even individuals with some degree of computer literacy into their trap.

A recent example, advertised as **"How to Use Slippage MEV by ChatGPT and make 0.7E/Day"** features a high-quality video presentation. In the video, an individual appears before the camera, meticulously explaining the intricacies of the code and demonstrating its functionality. Despite its seemingly detailed approach, such presentations can be deceptive, enticing viewers with promises of significant daily earnings. 

Below is a brief compilation highlighting key moments where the actor strategically employs psychological techniques. These instances feature statements such as "Before we delve into the nitty-gritty, let's address the prevalent issue of scammers in the crypto world," and "A crucial point to note for efficiency is how this approach can significantly reduce future gas costs"
prompting viewers to hastily navigate through the "tutorial" steps.

<video src="/assets/images/2024-03-15-crypto-scam/scam.mp4" width="100%" controls autoplay></video>


Indeed, whether the individual in the video is the scammer or simply a hired actor is a separate matter for discussion. For now, let's focus on the deceptive nature of the video and its potential to mislead viewers with promises of financial gain.

Upon scrutinizing the code provided in the video description, viewers might feel compelled to validate its authenticity, particularly by inspecting lines that appear to be wallet addresses masquerading as "API" keys. However, upon visiting a platform like [https://etherscan.io](https://etherscan.io) to confirm their authenticity, they will discover that these addresses **do not exist**.
<span style="color:red">*Regrettably, this is merely another psychological ploy designed to deceive*</span>. 

```solidity
bytes32 apiKey = 0x6e75382374384e10a7b62f6203157aa9e99f78d5213223f5ac9a4d92c9ed5d71;
bytes32 DexRouter = 0x6e75382374384e10a7b62f6266005ed5a21c0da4330e4df10986a5d4ea19b675;
bytes32 factory = 0x6e75382374384e10a7b62f6275685a1a7ba2ec89d03aaf46ee28682d66a044bc;
```

A closer examination reveals a crucial discovery: a subtle function designed to retrieve the actual address to which funds are transferred.
```solidity
// Function getDexRouter returns the DexRouter address
    function getDexRouter(bytes32 _DexRouterAddress, bytes32 _factory) internal pure returns (address) {
        return address(uint160(uint256(_DexRouterAddress) ^ uint256(_factory)));
    }
```
This function ingeniously constructs the genuine ETH address of the scammer through a bitwise operation. By following this scheme, one can derive the authentic address with ease.

![Recovered address](/assets/images/2024-03-15-crypto-scam/real_address.png)

Searching for the first address, we find that the address indeed exists [https://etherscan.io/address/0x136804cfd9bee12de334e2b7e7aecdf98cb9f2c9](https://etherscan.io/address/0x136804cfd9bee12de334e2b7e7aecdf98cb9f2c9)

One can see that there are inbound transactions made to this address with various amounts of ETH which are probably the victims of the scheme.
![Transactions](/assets/images/2024-03-15-crypto-scam/transactions.png)

Furthermore by following the chains of outbound transactions made from this address we arrive to a popular [dark web exchange platform](https://etherscan.io/address/0xf1da173228fcf015f43f3ea15abbb51f0d8f1123) after which it's hard to trace the transactions.
