Типы данных bool, uint, int  

    contract DataTypes {
    bool myBool;
`` myBool - state variable переменная состояния. Такая переменная будет храниться прямо в контракте.
Т.е она хранится в блокчейне и будет там до тех пор, пока блокчейн существует.
в Solidity не существует концепции "null", все переменные, которые когда-либо создаются, всегда имеют
значение по умолчанию.   
Переменные можно инициализировать при объявлении: bool myBool = true;
``

    function myFunc(bool _inputBool) {
        bool localBool = true;
``Операции с логическими переменными: ``

    localBool && inputBool;  - логическое И  
    localBool || inputBool;  - логическое ИЛИ
    localBool == inputBool;  - оператор равенства
    localBool == inputBool;  - оператор неравенства
    !localBool;  - логическое не
        
        }
    }

``Значения по умолчанию:  
bool = false  
``