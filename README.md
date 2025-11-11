## Experiment 1: Decentralized Certificate Verification
## Aim:
To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.

## Algorithm:

1.Deploy a smart contract where universities can issue certificates.

2.Store a hash of certificate data on-chain.

3.Provide a verification function that checks certificate authenticity.

4.Users can verify the certificate by comparing the stored hash.

## Program:
```
// SPDX-License-Identifier: MIT 
pragma solidity ^0.8.20; 
 
contract CertificateVerification { 
    address public university; 
    mapping(bytes32 => bool) public certificates; // Store hashed certificates 
 
    event CertificateIssued(bytes32 indexed certHash); 
 
    constructor() { 
        university = msg.sender; // University deploys the contract 
    } 
 
    function issueCertificate(string memory studentName, string memory degree, 
uint256 year) public { 
        require(msg.sender == university, "Only university can issue 
certificates"); 
        bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, 
year)); 
        certificates[certHash] = true; 
        emit CertificateIssued(certHash); 
    } 
 
    function verifyCertificate(string memory studentName, string memory degree, 
uint256 year) public view returns (bool) { 
        bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, 
year)); 
        return certificates[certHash]; 
    } 
}
```

## Output:

## True
<img width="1600" height="780" alt="image" src="https://github.com/user-attachments/assets/308aec32-b2c2-4526-b2fe-ae891098bc2a" />

## False :
<img width="1600" height="772" alt="image" src="https://github.com/user-attachments/assets/c2e69227-b5de-449b-92f7-88f23438e167" />

## Result:
Thus, the program to develop decentralized certificate verification is successfully executed.

