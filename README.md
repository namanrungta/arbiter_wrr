# arbiter_wrr
### Weighted Round Robin (WRR) with Atomic Lock



This arbitration logic combines **Quality of Service (QoS)** with **atomic operation support**. It grants access to clients in a fixed circular order, where each client is assigned a configurable "weight" that dictates how many consecutive clock cycles they may hold the bus (e.g., a weight of 3 allows 4 cycles of data transfer).

Crucially, it includes an **atomic lock override**:

* **Grant Extension:** The currently granted client can assert a `lock` signal to retain the bus indefinitely, overriding the weight counter to perform uninterrupted critical sequences (like Read-Modify-Write).
* **Strict Ownership:** The arbiter ignores lock assertions from waiting clients; only the current owner can lock the bus.
* **Work Conservation:** If a client releases the lock (or drops its request) before its time is up, the arbiter must immediately switch to the next requestor to prevent idle bus cycles.

**Would you like me to bundle all these files (Description, Prompt, Grader, Testbench, RTL) into a single directory structure format for easy copy-pasting?**
