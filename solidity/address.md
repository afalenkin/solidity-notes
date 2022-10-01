Address - адрес.

    contract MyShop {
    address myAddress = 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4;
    
    function getBalance(address inputAddress) public view returns(uint){
       return inputAddress.balance;
    }

``  myAddress.balance - получить баланс адреса. В блокчейне данные об адресвх и их счетах - публичны, поэтому с помощью ключевого слова balance можно узнать баланс любого адреса.``

    function transferTo(address inputAddress, uint amount) public {
        address payable _to = payable(inputAddress);
        _to.transfer(amount); // - не сработает
    }
``address.transfer(amount) - при вызове метода transfer у адреса мы можем перевести
на него указанное количество средств.  
Но просто так нельзя вызвать метод transfer, адрес, на который переводятся средства,
должен быть явно помечен как payable в аргументах метода, либо должен быть 
приведен к payable в теле функции.``

    function receiveFunds() public payable {

    }

``Функция, которая помечена payable - может принимать средства. Ее тело может быть пустым
и средства, с которыми кто-то вызовет эту функцию - автоматически будут зачислены на
счет контракта. Но при необходимости тело может содержать логику``

    }