# SNS launch steps

## Overview
At a high level, the stages for launching an SNS in production are explained [here](../launching/launch-summary-1proposal.md).

This article lists the technical commands and steps a developer needs to complete the stages for an SNS launch.

At a low level, the [SNS local testing repository](../testing/testing-locally.md) guides you
through the same, with the difference that the commands here target the canisters on the mainnet.

## Requirements

### 1. IC SDK

See: [installing the IC SDK](../../../setup/install).

### 2. `ic-admin`

See: [installing the `ic-admin`](../../../setup/ic-admin.md).

### 3. `sns` CLI

:::note
The version of the sns CLI that is bundled with your dfx version may not have the latest commands described in the Usage section. If needed, it is recommended to build and use the sns CLI tool yourself.
:::

```bash
git clone git@github.com:dfinity/ic.git
cd ic
bazel build //rs/sns/cli:sns
ls bazel-bin/rs/sns/cli/sns 
```
## Stages

### 1. Dapp developers choose the initial parameters of the SNS for a dapp

Typically, dapp developers choose initial parameters that will be used in subsequent proposals.

### 2. Submit NNS proposal to create SNS

Anyone who owns an eligible NNS neuron with enough stake can submit an NNS 
proposal to create an SNS for a given dapp.
Of course it is crucial to set the right parameters in this proposal.
You can also find an example how this command is used in the SNS local testing
[here](https://github.com/dfinity/sns-testing/blob/main/propose_sns.sh).

To create such a proposal, a common path is to use `sns-cli` and run the following:
```
dfx sns propose --network ic --neuron $NEURON_ID sns_init.yaml
```

### 3. Dapp developers add NNS root as co-controller of dapp

They can do so by running the following command:
```
dfx sns prepare-canisters add-nns-root $CANISTER_ID
```

### 4. The NNS proposal is decided
Nothing technical for dapp developers to do. Community votes.


### 5. (Automated) SNS-W deploys SNS canisters
Nothing technical for dapp developers to do. This is triggered automatically as a result
of an adopted proposal in Stage 4.

### 6. (Automated) SNS-W sets SNS root as sole controller of dapp
Nothing technical for dapp developers to do. This is triggered automatically as a result
of an adopted proposal in Stage 4.

### 7. (Automated) SNS-W initializes SNS canisters according to settings from Step 1
Nothing technical for dapp developers to do. This is triggered automatically as a result
of an adopted proposal in Stage 4.

### 8. (Automated) SNS swap starts
Nothing technical for dapp developers to do. This is triggered automatically as a result
of an adopted proposal in Stage 4.

### 9. (Automated) SNS swap ends
Nothing technical for dapp developers to do. This is triggered automatically as a result
of an adopted proposal in Stage 4.

### 10. (Automated) SNS swap finalizes
Nothing technical for dapp developers to do. This is triggered automatically as a result
of an adopted proposal in Stage 4.