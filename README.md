# Cortado

<div align="center">
  <img src="public/cortado.png" alt="Cortado Logo" width="200"/>
</div>

A comprehensive test suite library for foundry projects that provides enhanced testing utilities, assertions, and development tools for Ethereum smart contract testing.

## Overview

Cortado is a foundry testing library designed to streamline and enhance the testing experience for smart contract development. It provides a rich set of testing utilities, custom assertions, and helper functions that extend foundry's built-in testing capabilities, making tests more readable, maintainable, and comprehensive.

## Core Features

- **Enhanced Testing Utilities**: Extended Test contract with powerful testing helpers
- **Advanced Assertions**: Custom assertion functions for common DeFi and smart contract patterns
- **Token Testing Helpers**: Utilities for ERC20/ERC721/ERC1155 testing scenarios
- **Gas Measurement Tools**: Built-in gas profiling and optimization helpers
- **Security Testing**: Common vulnerability testing patterns and helpers
- **Time Manipulation**: Advanced time-warp and block manipulation utilities
- **State Management**: Snapshot and rollback utilities for complex test scenarios

## Installation

```bash
forge install pxlvre/cortado
```

## Quick Start

```solidity
import {CortadoTest as Test} from "cortado/CortadoTest.sol";

contract MyContractTest is Test {
    function testTokenTransfer() public {
        // Enhanced assertions
        assertApproxEqRel(actualAmount, expectedAmount, 0.01e18); // 1% tolerance
        
        // Gas measurement
        uint256 gasBefore = measureGas();
        myContract.expensiveFunction();
        uint256 gasUsed = measureGas() - gasBefore;
        
        // Time manipulation
        timeWarp(1 days);
        
        // Token helpers
        dealTokens(USDC, alice, 1000e6);
        assertBalanceChange(USDC, alice, -100e6, () => {
            myContract.withdraw(100e6);
        });
    }
}
```

## Testing Categories

### Basic Testing Utilities
- Enhanced assertions and comparisons
- Improved error handling and debugging
- Better test organization and structure

### DeFi Testing Tools
- Liquidity pool testing helpers
- Price oracle mocking utilities
- Yield farming scenario testing
- Slippage and MEV protection testing

### Security Testing
- Reentrancy attack simulation
- Access control testing patterns
- Overflow/underflow protection testing
- Front-running and sandwich attack scenarios

### Gas Optimization
- Automated gas profiling
- Gas usage regression testing
- Optimization suggestion tools

## License

This project is licensed under the [AGPL-3.0](LICENSE) license.

The choice of AGPL-3.0 aligns with the principles outlined by Vitalik Buterin in his post ["Why I used to prefer permissive licenses and now favor copyleft"](https://vitalik.eth.limo/general/2025/07/07/copyleft.html), ensuring that improvements and derivatives remain open and accessible to the community.

## Contributing

Contributions are welcome! Please ensure all contributions maintain the open-source spirit of this project.

## Development

```bash
# Build
forge build

# Test
forge test

# Format
forge fmt

# Test with coverage
forge coverage
```

## Integration with Prosciutto

Cortado is designed to work seamlessly with [Prosciutto](https://github.com/pxlvre/prosciutto), providing enhanced testing capabilities for projects using Prosciutto's DevOps utilities.

```solidity
import {CortadoTest} from "cortado/CortadoTest.sol";
import {ProScript} from "prosciutto/ProScript.sol";

contract DeploymentTest is CortadoTest {
    function testDeploymentIntegration() public {
        // Use Prosciutto for deployment management
        // Use Cortado for enhanced testing
    }
}
```