## ICP Ledger types
### Install
```
mops add ledger-types
```

### Import
```motoko
import Ledger "mo:ledger-types";

let ledger = actor("ryjl3-tyaaa-aaaaa-aaaba-cai") : Ledger.Service;
```

### Usage examples

#### Check ICP balance
```motoko
let result = await ledger.account_balance({ account = accountId });

// handle result.e8s
```

#### Transfer ICP tokens
```motoko
let result : Ledger.TransferResult = await ledger.transfer({
	to = accountId;
	fee = { e8s = 10_000 };
	memo = 0;
	from_subaccount = null;
	created_at_time = null;
	amount = { e8s = 1_000_000 };
});

switch (result) {
	case (#Ok(blockIndex)) {
		// sent at blockIndex
	};
	case (#Err(err)) {
		// handle error
	};
};
```