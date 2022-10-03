Для тестирования как минимум потребуются Hardhat, Waffle, Ethers, Mocha, Chai.  
Предварительно также нужно установить node.  
Для тестирования смарт-контрактов нужно инициировать проект hardhat. Контракты должны храниться в 
пакете contracts, тесты в директорию test.  
Смартконтракты можно компилировать выполнив команду npx hardhat compile в корне проекта. При этом выполнится
операция, аналогичная компиляции контракта в IDE Remix.  

Рассмотрим тестирование простейшего смартконтракта:  

// SPDX-License-Identifier: GPL-3.0

pragma solidity ^0.8.0;


    contract Payments {
    
        struct Payment {
            uint amount;
            uint timestamp;
            address from;
            string message;
        }
    
        struct Balance {
            uint totalPayments;
            mapping(uint => Payment) payments;
        }
    
        mapping(address => Balance) balances;
    
        function currentBalance () public view returns(uint) {
            return address(this).balance;
        }
    
        function getPayment(address _addr, uint _index) public view returns(Payment memory) {
            return balances[_addr].payments[_index];
        }
    
        function pay(string memory message) public payable {
            uint paymentNum = balances[msg.sender].totalPayments;
            balances[msg.sender].totalPayments++;
    
            Payment memory newPayment = Payment(
                msg.value,
                block.timestamp,
                msg.sender,
                message
            );
    
            balances[msg.sender].payments[paymentNum] = newPayment;
        } 
    }
   

