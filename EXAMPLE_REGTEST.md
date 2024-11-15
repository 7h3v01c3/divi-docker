# How to Use Regtest Mode with Divi Docker Image

This guide demonstrates how to run the Divi Docker container to connect to the Divi Regtest Environment.

---

## What is Regtest Mode?

Regtest (short for "Regression Testing Mode") is a special mode designed for developers and testers. It creates a local, private blockchain environment isolated from public networks such as mainnet or testnet.

### Key Characteristics of Regtest Mode:
- **Instant Block Creation**: Blocks can be generated on demand, enabling rapid testing without waiting for confirmations.
- **No Network Connection**: The blockchain operates entirely offline and is private.
- **Customizable Parameters**: Developers can configure block intervals, consensus, and other blockchain parameters.
- **Low Resource Requirements**: Regtest demands fewer system resources compared to mainnet.

### Why is Regtest Easier and Faster for Development?
1. **Speed**: Instantly generate blocks using commands like `setgenerate`.
2. **Isolation**: Test in a controlled environment without external interference.
3. **Reproducibility**: Easily replicate tests due to full control over the blockchain.
4. **No Costs**: No transaction fees; coins are created for free.
5. **Debugging**: Experiment and debug without impacting live chains or risking vulnerabilities.

---

## Basic Usage

To run the Divi Docker container with regtest mode enabled, use the following command:

```bash
docker run -d --name divid_container \
    -e "DIVI_REGTEST=true" \
    divi_v2
```

### Command Breakdown:
- `docker run`: Command to start a Docker container.
- `-d`: Run the container in detached mode (in the background).
- `--name divid_container`: Assign a name to the container for easier management.
- `-e "DIVI_REGTEST=true"`: Set an environment variable to enable regtest mode.
- `divi_v2`: The Docker image name for the Divi daemon.

---

## Example Commands

### Example - `getinfo`

To retrieve node information, use:

```bash
/ # divi-cli getinfo
```

Sample output:

```json
{
    "version": "3.0.0.0",
    "protocolversion": 70915,
    "walletversion": 120200,
    "balance": 0.00000000,
    "blocks": 0,
    "timeoffset": 0,
    "connections": 0,
    "proxy": "",
    "difficulty": 0.00000000,
    "testnet": false,
    "moneysupply": 0.00000000,
    "relayfee": 0.00010000,
    "staking status": "Staking Not Active",
    "errors": ""
}
```

---

### Example - `setgenerate`

To generate blocks in regtest mode, use:

```bash
/ # divi-cli setgenerate 1000
```

Sample output:

```json
[
    "5ed6996b1b31aa2b66b5f3bd597bc9d4e2a15b6ce0709641662a4b9b293e73ff",
    "0f1138327c14d5ac38d432fdcf45644288fde575e7fdab6b18abd0e361be02d9",
    ...
    "21cd9c51ed5d17d86033405287e4dc1b83e1ccc10599faf2aaa97a6088a3fbb3",
    "561f618e62bac2e22867c4c54b752d37a0f0ef02941122682025b3a0fce6105b"
]
```

---

## Benefits of Using Docker for Regtest

1. **Simplified Setup**: Docker packages all dependencies, avoiding installation issues.
2. **Isolation**: The node runs in a self-contained environment, ensuring it doesn't interfere with your host system or other blockchain instances.
3. **Portability**: Docker images can be easily shared and reused across systems.
4. **Clean Environment**: Containers can be stopped, restarted, or removed without leaving residual files.
