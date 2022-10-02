struct - сложные структуры данных.   

    contract Demo {
    
    // Struct
    struct Payment {
    uint amount;
    uint timestamp;
    address from;
    string message;
    
           // Payment payment; - запрещено создавать рекурсивные типы(которые включают сами себя в качестве поля).
    }
    
    struct Balance {
    uint totalPayments;
    mapping (unt => Payment) payments;
    }
    
    mapping (address => Balance) public balances;
    
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
    
    function getPayment(address _addr, uint _index) public view returns(Payment memory){
    return balances[_addr].payments[_index];
    
    }
    
    }