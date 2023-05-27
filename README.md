# Counter
The "Counter" module is a configurable counter that can increment, decrement, or load a binary value based on control signals.
It provides a counter output that represents the current count value.

# * Register Initialization:

The module uses a D flip-flop (Q_reg) to store the current counter value.
On the positive edge of the clock (clk) and the negative edge of the reset signal (reset_n), the module initializes the counter.
When the reset signal is asserted (low logic level), the counter is reset to zero ('b0) to ensure a known starting point.
When the enable signal (enb) is asserted, the counter is updated with the next value (Q_next) calculated in the following steps.
When the enable signal is not asserted, the counter value remains unchanged to hold the current count value.

# * Counter Logic:

The module uses combinational logic to calculate the next counter value (Q_next) based on the current counter value (Q_reg),
up/down control signal (up_Down), parallel enable signal (pe), and parallel input data (pi).
The control signals determine the operation to be performed on the counter:
* 2'b00 - Count down: The counter value is decremented by 1 (Q_next = Q_reg - 1).
* 2'bx1 - Load parallel input: The counter value is replaced with the parallel input data (pi) provided at the input (Q_next = pi).
* 2'b10 - Count up: The counter value is incremented by 1 (Q_next = Q_reg + 1).
* Default case: The counter value remains unchanged (Q_next = Q_reg).
The calculated next value (Q_next) is stored in the register (Q_reg) on the next positive edge of the clock (clk).

# * Output Assignment:

The final output (Q) is assigned the value stored in the register (Q_reg), representing the current counter value.
The counter output (Q) is available for further processing or can be connected to other components within the larger system.
By configuring the control signals (up_Down, pe) and providing parallel input data (pi),
you can control the behavior of the counter. It can be used for tasks such as sequencing,
event counting, timekeeping, or any application that requires tracking and manipulating a binary count value.

It's important to note that the module's behavior depends on the specific control signals and input data provided,
allowing flexibility in counting modes and parallel loading.
The module can be instantiated with different parameter values (n) to adjust the bit width of the counter based on the desired application requirements.
