# Complete the stake, redeem, and claim flow (including 6hr unbonding)

To complete this task you will have to submit all 3 transactions (stake, redeem, claim) into the task form : [SUBMISSION FORM](https://forms.gle/urhJDEkqfMM9h1367)

# 1. Add liquid stake

Liquid stake your ATOM on Stride for stATOM. Here's an example of how to liquid stake. Change `<WALLET>` to your wallet name from `strided keys list`

```
strided tx stakeibc liquid-stake 1000 uatom --from <WALLET> --chain-id STRIDE-TESTNET-2
```

# 2. Redeem stake
After accruing some staking rewards, you can unstake your tokens. Currently, the unbonding period on our Gaia (Cosmos Hub) testnet is around 6 hours.
```
strided tx stakeibc redeem-stake 1000 GAIA <COSMOS_ADDRESS_YOU_WANT_TO_REDEEM_TO> --chain-id STRIDE-TESTNET-2 --from <WALLET>
```

# 3. Check if tokens are claimable
Change stride15rdc0pzpr4x88wee3tjlu6f2alknh79ph03y2t to your stride wallet address
```
strided q records list-user-redemption-record --limit 10000 --output json | jq '.UserRedemptionRecord | map(select(.sender == "stride15rdc0pzpr4x88wee3tjlu6f2alknh79ph03y2t"))'
```
OUTPUT:

NOTE:
If your record has the attribute `isClaimable=true`, they're ready to be claimed!
Here you also can find all attributes that will be needed to claim your stake at the next step

# 4. Claim your stake
You will need `hostZoneId`, `epochNumber` and `sender` from previous step. Change `<WALLET>` to your wallet name from `strided keys list`
```
strided tx stakeibc claim-undelegated-tokens GAIA 280 stride15rdc0pzpr4x88wee3tjlu6f2alknh79ph03y2t --chain-id STRIDE-TESTNET-2 --from <WALLET> --yes
```
# 5. Submit the transaction hash
