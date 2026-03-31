# TimeLock-Wallet
TimeLock Wallet
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract TimeLock {
    uint256 public unlockTime;

    constructor(uint256 _unlockTime) payable {
        unlockTime = _unlockTime;
    }

    function withdraw() public {
        require(block.timestamp >= unlockTime, "Locked");
        payable(msg.sender).transfer(address(this).balance);
    }
}
