# Snapshot report for `src/erc20.test.ts`

The actual snapshot is saved in `erc20.test.ts.snap`.

Generated by [AVA](https://avajs.dev).

## basic erc20

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Permit {␊
        constructor() ERC20("MyToken", "MTK") ERC20Permit("MyToken") {}␊
    }␊
    `

## erc20 burnable

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Burnable} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Burnable, ERC20Permit {␊
        constructor() ERC20("MyToken", "MTK") ERC20Permit("MyToken") {}␊
    }␊
    `

## erc20 pausable

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Pausable} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Pausable.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    import {Ownable} from "@openzeppelin/contracts/access/Ownable.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Pausable, Ownable, ERC20Permit {␊
        constructor(address initialOwner)␊
            ERC20("MyToken", "MTK")␊
            Ownable(initialOwner)␊
            ERC20Permit("MyToken")␊
        {}␊
    ␊
        function pause() public onlyOwner {␊
            _pause();␊
        }␊
    ␊
        function unpause() public onlyOwner {␊
            _unpause();␊
        }␊
    ␊
        // The following functions are overrides required by Solidity.␊
    ␊
        function _update(address from, address to, uint256 value)␊
            internal␊
            override(ERC20, ERC20Pausable)␊
        {␊
            super._update(from, to, value);␊
        }␊
    }␊
    `

## erc20 pausable with roles

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {AccessControl} from "@openzeppelin/contracts/access/AccessControl.sol";␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Pausable} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Pausable.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Pausable, AccessControl, ERC20Permit {␊
        bytes32 public constant PAUSER_ROLE = keccak256("PAUSER_ROLE");␊
    ␊
        constructor(address defaultAdmin, address pauser)␊
            ERC20("MyToken", "MTK")␊
            ERC20Permit("MyToken")␊
        {␊
            _grantRole(DEFAULT_ADMIN_ROLE, defaultAdmin);␊
            _grantRole(PAUSER_ROLE, pauser);␊
        }␊
    ␊
        function pause() public onlyRole(PAUSER_ROLE) {␊
            _pause();␊
        }␊
    ␊
        function unpause() public onlyRole(PAUSER_ROLE) {␊
            _unpause();␊
        }␊
    ␊
        // The following functions are overrides required by Solidity.␊
    ␊
        function _update(address from, address to, uint256 value)␊
            internal␊
            override(ERC20, ERC20Pausable)␊
        {␊
            super._update(from, to, value);␊
        }␊
    }␊
    `

## erc20 pausable with managed

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {AccessManaged} from "@openzeppelin/contracts/access/manager/AccessManaged.sol";␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Pausable} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Pausable.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Pausable, AccessManaged, ERC20Permit {␊
        constructor(address initialAuthority)␊
            ERC20("MyToken", "MTK")␊
            AccessManaged(initialAuthority)␊
            ERC20Permit("MyToken")␊
        {}␊
    ␊
        function pause() public restricted {␊
            _pause();␊
        }␊
    ␊
        function unpause() public restricted {␊
            _unpause();␊
        }␊
    ␊
        // The following functions are overrides required by Solidity.␊
    ␊
        function _update(address from, address to, uint256 value)␊
            internal␊
            override(ERC20, ERC20Pausable)␊
        {␊
            super._update(from, to, value);␊
        }␊
    }␊
    `

## erc20 burnable pausable

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Burnable} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";␊
    import {ERC20Pausable} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Pausable.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    import {Ownable} from "@openzeppelin/contracts/access/Ownable.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Burnable, ERC20Pausable, Ownable, ERC20Permit {␊
        constructor(address initialOwner)␊
            ERC20("MyToken", "MTK")␊
            Ownable(initialOwner)␊
            ERC20Permit("MyToken")␊
        {}␊
    ␊
        function pause() public onlyOwner {␊
            _pause();␊
        }␊
    ␊
        function unpause() public onlyOwner {␊
            _unpause();␊
        }␊
    ␊
        // The following functions are overrides required by Solidity.␊
    ␊
        function _update(address from, address to, uint256 value)␊
            internal␊
            override(ERC20, ERC20Pausable)␊
        {␊
            super._update(from, to, value);␊
        }␊
    }␊
    `

## erc20 preminted

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Permit {␊
        constructor(address recipient)␊
            ERC20("MyToken", "MTK")␊
            ERC20Permit("MyToken")␊
        {␊
            _mint(recipient, 1000 * 10 ** decimals());␊
        }␊
    }␊
    `

## erc20 premint of 0

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Permit {␊
        constructor() ERC20("MyToken", "MTK") ERC20Permit("MyToken") {}␊
    }␊
    `

## erc20 mintable

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    import {Ownable} from "@openzeppelin/contracts/access/Ownable.sol";␊
    ␊
    contract MyToken is ERC20, Ownable, ERC20Permit {␊
        constructor(address initialOwner)␊
            ERC20("MyToken", "MTK")␊
            Ownable(initialOwner)␊
            ERC20Permit("MyToken")␊
        {}␊
    ␊
        function mint(address to, uint256 amount) public onlyOwner {␊
            _mint(to, amount);␊
        }␊
    }␊
    `

## erc20 mintable with roles

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {AccessControl} from "@openzeppelin/contracts/access/AccessControl.sol";␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    ␊
    contract MyToken is ERC20, AccessControl, ERC20Permit {␊
        bytes32 public constant MINTER_ROLE = keccak256("MINTER_ROLE");␊
    ␊
        constructor(address defaultAdmin, address minter)␊
            ERC20("MyToken", "MTK")␊
            ERC20Permit("MyToken")␊
        {␊
            _grantRole(DEFAULT_ADMIN_ROLE, defaultAdmin);␊
            _grantRole(MINTER_ROLE, minter);␊
        }␊
    ␊
        function mint(address to, uint256 amount) public onlyRole(MINTER_ROLE) {␊
            _mint(to, amount);␊
        }␊
    }␊
    `

## erc20 permit

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Permit {␊
        constructor() ERC20("MyToken", "MTK") ERC20Permit("MyToken") {}␊
    }␊
    `

## erc20 votes

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    import {ERC20Votes} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Votes.sol";␊
    import {Nonces} from "@openzeppelin/contracts/utils/Nonces.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Permit, ERC20Votes {␊
        constructor() ERC20("MyToken", "MTK") ERC20Permit("MyToken") {}␊
    ␊
        // The following functions are overrides required by Solidity.␊
    ␊
        function _update(address from, address to, uint256 value)␊
            internal␊
            override(ERC20, ERC20Votes)␊
        {␊
            super._update(from, to, value);␊
        }␊
    ␊
        function nonces(address owner)␊
            public␊
            view␊
            override(ERC20Permit, Nonces)␊
            returns (uint256)␊
        {␊
            return super.nonces(owner);␊
        }␊
    }␊
    `

## erc20 votes + blocknumber

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    import {ERC20Votes} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Votes.sol";␊
    import {Nonces} from "@openzeppelin/contracts/utils/Nonces.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Permit, ERC20Votes {␊
        constructor() ERC20("MyToken", "MTK") ERC20Permit("MyToken") {}␊
    ␊
        // The following functions are overrides required by Solidity.␊
    ␊
        function _update(address from, address to, uint256 value)␊
            internal␊
            override(ERC20, ERC20Votes)␊
        {␊
            super._update(from, to, value);␊
        }␊
    ␊
        function nonces(address owner)␊
            public␊
            view␊
            override(ERC20Permit, Nonces)␊
            returns (uint256)␊
        {␊
            return super.nonces(owner);␊
        }␊
    }␊
    `

## erc20 votes + timestamp

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    import {ERC20Votes} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Votes.sol";␊
    import {Nonces} from "@openzeppelin/contracts/utils/Nonces.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Permit, ERC20Votes {␊
        constructor() ERC20("MyToken", "MTK") ERC20Permit("MyToken") {}␊
    ␊
        function clock() public view override returns (uint48) {␊
            return uint48(block.timestamp);␊
        }␊
    ␊
        // solhint-disable-next-line func-name-mixedcase␊
        function CLOCK_MODE() public pure override returns (string memory) {␊
            return "mode=timestamp";␊
        }␊
    ␊
        // The following functions are overrides required by Solidity.␊
    ␊
        function _update(address from, address to, uint256 value)␊
            internal␊
            override(ERC20, ERC20Votes)␊
        {␊
            super._update(from, to, value);␊
        }␊
    ␊
        function nonces(address owner)␊
            public␊
            view␊
            override(ERC20Permit, Nonces)␊
            returns (uint256)␊
        {␊
            return super.nonces(owner);␊
        }␊
    }␊
    `

## erc20 flashmint

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import {ERC20FlashMint} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20FlashMint.sol";␊
    import {ERC20Permit} from "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Permit, ERC20FlashMint {␊
        constructor() ERC20("MyToken", "MTK") ERC20Permit("MyToken") {}␊
    }␊
    `

## erc20 full upgradeable transparent

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {AccessControlUpgradeable} from "@openzeppelin/contracts-upgradeable/access/AccessControlUpgradeable.sol";␊
    import {ERC20Upgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";␊
    import {ERC20BurnableUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20BurnableUpgradeable.sol";␊
    import {ERC20FlashMintUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20FlashMintUpgradeable.sol";␊
    import {ERC20PausableUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20PausableUpgradeable.sol";␊
    import {ERC20PermitUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20PermitUpgradeable.sol";␊
    import {ERC20VotesUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";␊
    import {Initializable} from "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";␊
    import {NoncesUpgradeable} from "@openzeppelin/contracts-upgradeable/utils/NoncesUpgradeable.sol";␊
    ␊
    contract MyToken is Initializable, ERC20Upgradeable, ERC20BurnableUpgradeable, ERC20PausableUpgradeable, AccessControlUpgradeable, ERC20PermitUpgradeable, ERC20VotesUpgradeable, ERC20FlashMintUpgradeable {␊
        bytes32 public constant PAUSER_ROLE = keccak256("PAUSER_ROLE");␊
        bytes32 public constant MINTER_ROLE = keccak256("MINTER_ROLE");␊
    ␊
        /// @custom:oz-upgrades-unsafe-allow constructor␊
        constructor() {␊
            _disableInitializers();␊
        }␊
    ␊
        function initialize(address defaultAdmin, address pauser, address recipient, address minter)␊
            public initializer␊
        {␊
            __ERC20_init("MyToken", "MTK");␊
            __ERC20Burnable_init();␊
            __ERC20Pausable_init();␊
            __AccessControl_init();␊
            __ERC20Permit_init("MyToken");␊
            __ERC20Votes_init();␊
            __ERC20FlashMint_init();␊
    ␊
            _grantRole(DEFAULT_ADMIN_ROLE, defaultAdmin);␊
            _grantRole(PAUSER_ROLE, pauser);␊
            _mint(recipient, 2000 * 10 ** decimals());␊
            _grantRole(MINTER_ROLE, minter);␊
        }␊
    ␊
        function pause() public onlyRole(PAUSER_ROLE) {␊
            _pause();␊
        }␊
    ␊
        function unpause() public onlyRole(PAUSER_ROLE) {␊
            _unpause();␊
        }␊
    ␊
        function mint(address to, uint256 amount) public onlyRole(MINTER_ROLE) {␊
            _mint(to, amount);␊
        }␊
    ␊
        // The following functions are overrides required by Solidity.␊
    ␊
        function _update(address from, address to, uint256 value)␊
            internal␊
            override(ERC20Upgradeable, ERC20PausableUpgradeable, ERC20VotesUpgradeable)␊
        {␊
            super._update(from, to, value);␊
        }␊
    ␊
        function nonces(address owner)␊
            public␊
            view␊
            override(ERC20PermitUpgradeable, NoncesUpgradeable)␊
            returns (uint256)␊
        {␊
            return super.nonces(owner);␊
        }␊
    }␊
    `

## erc20 full upgradeable uups

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {AccessControlUpgradeable} from "@openzeppelin/contracts-upgradeable/access/AccessControlUpgradeable.sol";␊
    import {ERC20Upgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";␊
    import {ERC20BurnableUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20BurnableUpgradeable.sol";␊
    import {ERC20FlashMintUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20FlashMintUpgradeable.sol";␊
    import {ERC20PausableUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20PausableUpgradeable.sol";␊
    import {ERC20PermitUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20PermitUpgradeable.sol";␊
    import {ERC20VotesUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";␊
    import {Initializable} from "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";␊
    import {NoncesUpgradeable} from "@openzeppelin/contracts-upgradeable/utils/NoncesUpgradeable.sol";␊
    import {UUPSUpgradeable} from "@openzeppelin/contracts-upgradeable/proxy/utils/UUPSUpgradeable.sol";␊
    ␊
    contract MyToken is Initializable, ERC20Upgradeable, ERC20BurnableUpgradeable, ERC20PausableUpgradeable, AccessControlUpgradeable, ERC20PermitUpgradeable, ERC20VotesUpgradeable, ERC20FlashMintUpgradeable, UUPSUpgradeable {␊
        bytes32 public constant PAUSER_ROLE = keccak256("PAUSER_ROLE");␊
        bytes32 public constant MINTER_ROLE = keccak256("MINTER_ROLE");␊
        bytes32 public constant UPGRADER_ROLE = keccak256("UPGRADER_ROLE");␊
    ␊
        /// @custom:oz-upgrades-unsafe-allow constructor␊
        constructor() {␊
            _disableInitializers();␊
        }␊
    ␊
        function initialize(address defaultAdmin, address pauser, address recipient, address minter, address upgrader)␊
            public initializer␊
        {␊
            __ERC20_init("MyToken", "MTK");␊
            __ERC20Burnable_init();␊
            __ERC20Pausable_init();␊
            __AccessControl_init();␊
            __ERC20Permit_init("MyToken");␊
            __ERC20Votes_init();␊
            __ERC20FlashMint_init();␊
            __UUPSUpgradeable_init();␊
    ␊
            _grantRole(DEFAULT_ADMIN_ROLE, defaultAdmin);␊
            _grantRole(PAUSER_ROLE, pauser);␊
            _mint(recipient, 2000 * 10 ** decimals());␊
            _grantRole(MINTER_ROLE, minter);␊
            _grantRole(UPGRADER_ROLE, upgrader);␊
        }␊
    ␊
        function pause() public onlyRole(PAUSER_ROLE) {␊
            _pause();␊
        }␊
    ␊
        function unpause() public onlyRole(PAUSER_ROLE) {␊
            _unpause();␊
        }␊
    ␊
        function mint(address to, uint256 amount) public onlyRole(MINTER_ROLE) {␊
            _mint(to, amount);␊
        }␊
    ␊
        function _authorizeUpgrade(address newImplementation)␊
            internal␊
            override␊
            onlyRole(UPGRADER_ROLE)␊
        {}␊
    ␊
        // The following functions are overrides required by Solidity.␊
    ␊
        function _update(address from, address to, uint256 value)␊
            internal␊
            override(ERC20Upgradeable, ERC20PausableUpgradeable, ERC20VotesUpgradeable)␊
        {␊
            super._update(from, to, value);␊
        }␊
    ␊
        function nonces(address owner)␊
            public␊
            view␊
            override(ERC20PermitUpgradeable, NoncesUpgradeable)␊
            returns (uint256)␊
        {␊
            return super.nonces(owner);␊
        }␊
    }␊
    `

## erc20 full upgradeable uups managed

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    // Compatible with OpenZeppelin Contracts ^5.0.0␊
    pragma solidity ^0.8.22;␊
    ␊
    import {AccessManagedUpgradeable} from "@openzeppelin/contracts-upgradeable/access/manager/AccessManagedUpgradeable.sol";␊
    import {ERC20Upgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";␊
    import {ERC20BurnableUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20BurnableUpgradeable.sol";␊
    import {ERC20FlashMintUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20FlashMintUpgradeable.sol";␊
    import {ERC20PausableUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20PausableUpgradeable.sol";␊
    import {ERC20PermitUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20PermitUpgradeable.sol";␊
    import {ERC20VotesUpgradeable} from "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";␊
    import {Initializable} from "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";␊
    import {NoncesUpgradeable} from "@openzeppelin/contracts-upgradeable/utils/NoncesUpgradeable.sol";␊
    import {UUPSUpgradeable} from "@openzeppelin/contracts-upgradeable/proxy/utils/UUPSUpgradeable.sol";␊
    ␊
    contract MyToken is Initializable, ERC20Upgradeable, ERC20BurnableUpgradeable, ERC20PausableUpgradeable, AccessManagedUpgradeable, ERC20PermitUpgradeable, ERC20VotesUpgradeable, ERC20FlashMintUpgradeable, UUPSUpgradeable {␊
        /// @custom:oz-upgrades-unsafe-allow constructor␊
        constructor() {␊
            _disableInitializers();␊
        }␊
    ␊
        function initialize(address initialAuthority, address recipient)␊
            public initializer␊
        {␊
            __ERC20_init("MyToken", "MTK");␊
            __ERC20Burnable_init();␊
            __ERC20Pausable_init();␊
            __AccessManaged_init(initialAuthority);␊
            __ERC20Permit_init("MyToken");␊
            __ERC20Votes_init();␊
            __ERC20FlashMint_init();␊
            __UUPSUpgradeable_init();␊
    ␊
            _mint(recipient, 2000 * 10 ** decimals());␊
        }␊
    ␊
        function pause() public restricted {␊
            _pause();␊
        }␊
    ␊
        function unpause() public restricted {␊
            _unpause();␊
        }␊
    ␊
        function mint(address to, uint256 amount) public restricted {␊
            _mint(to, amount);␊
        }␊
    ␊
        function _authorizeUpgrade(address newImplementation)␊
            internal␊
            override␊
            restricted␊
        {}␊
    ␊
        // The following functions are overrides required by Solidity.␊
    ␊
        function _update(address from, address to, uint256 value)␊
            internal␊
            override(ERC20Upgradeable, ERC20PausableUpgradeable, ERC20VotesUpgradeable)␊
        {␊
            super._update(from, to, value);␊
        }␊
    ␊
        function nonces(address owner)␊
            public␊
            view␊
            override(ERC20PermitUpgradeable, NoncesUpgradeable)␊
            returns (uint256)␊
        {␊
            return super.nonces(owner);␊
        }␊
    }␊
    `
