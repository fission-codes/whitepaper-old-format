Smart contract programming has been largely written by developers with primarily a traditional web background. Tooling and perspective is often limiuted to a classic single-application mindset, not taking stock of the unique tradeoffs of running on a global system.

# Status Codes

# CQRS: Command / Query Separation

* Queries can run lcoally for free / gasless
*

## State Reuse

> NB these diagrams are conceptual, and actual implementation may combine layers into a single smart contract

As is becoming imncreasingly common, splittingh state from behaviour encourages reuse, behaviour upgradability, &c. This pattern is not unlike a networked database in a traditional microservice architecture.

```
       State
         ^
         |
         v
   Access Control
    ^         ^
    |         |
    v         v
Client A    Client B
```

This `Access Control` layer may communicate over subcalls using the same protocol (ERC-902), which may in turn depend on state provided by other third parties (e.g. read only access, principle of least access, &c).

```
+---------Database----------+
|                           |
|         State A           |
|            ^              |
|            |              |
|            v              |
| +----Access Control-----+ |
| |                       | |
| | [✓] ACL B <-----------------erc902----> Auth Server A (Read Only)
| |                       | |
| | [✓] ACL B <-----------------erc902----> Auth Server B (Read Only)
| |                       | |
| | [✓] ACL C (Stateless) | |
| |                       | |
| +-----------------------+ |
|                           |
+---------------------------+
```

# Call Recursion



# Ad Hoc Composition / "Anonymous Contracts"

## Combinators