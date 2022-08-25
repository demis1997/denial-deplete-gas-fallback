# denial-deplete-gas-fallback
 create a fallback function to deplete the gas. Can also be done using assert

The key to this is that calls to outside contracts can create denial of service attacks. In this case by depleting the gas. This happens because no fixed gas stipend is being used. We can also check checks-effects-interactiosn pattern to stop not only denial of service but re entrancy as well.
In the case of this contract, we set the withdraw partner which we find in the functions and the contract abi as our external contract address. Within our external contract we create a fallback function, a while loop with empty code so that it reiterates back to it. When the withdraw partner is set to our contract, the gas in the target contract is depleted thus causing a denial of service attack. Similarly to ddos attacks on the network where the network has no more power left to compute actions, In solidity, no more gas left to compute causes the same effect.

await contract.setWithdrawPartner
