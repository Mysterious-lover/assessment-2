# assessment-2
metacrafters is assessemts are there:=

contract MyToken {
    string public tokenName;
    string public tokenAbbrv;
    uint public totalSupply;
    mapping(address => uint) public balances;

   constructor(string memory _tokenName, string memory _tokenAbbrv, uint _totalSupply) {
        tokenName = _tokenName;
        tokenAbbrv = _tokenAbbrv;
        totalSupply = _totalSupply;
        balances[msg.sender] = totalSupply;
    }

  function mint(address _to, uint _value) public {
        require(balances[_to] + _value > balances[_to], "Overflow");
        totalSupply += _value;
        balances[_to] += _value;
    }

  function burn(address _from, uint _value) public {
        require(balances[_from] >= _value, "Insufficient balance");
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}
