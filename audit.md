# Review DegenLockToken.sol

## Hash: 7c0977a79ef9e48480108f34a3d481f99346cc00

| **Severity**  | **Issue**                                    | **Description**                                                                                             | **Recommendation**                                                                                                          |
|---------------|----------------------------------------------|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| High          | Owner Can Extend Lock Duration               | The owner can change `lockDuration`, affecting all current deposits and potentially locking funds maliciously.| Restrict changes to affect only new deposits or use decentralized governance for such changes.                              |
| Medium        | Missing Events for Critical Actions          | No events emitted for `deposit` and `withdraw`.                                                             | Emit appropriate events for `deposit` and `withdraw` functions to ensure transparency.                                      |
| Informational        | Hardcoded Token Address                      | Limits flexibility as the token address is hardcoded.                                                       | Pass the token address as a parameter to the constructor for flexibility.                                                   |

### Recommendation

 `updateLockDuration` could be split.

* `killSwitch` function to set all to 0
* `updateLockDuraiton` based on newcomers, checked via mapping
