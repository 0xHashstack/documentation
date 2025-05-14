# Automated Liquidity Provision

We intended for the entire loan amount to be divided and allocated to the user's preferred liquidity pool. Ideally, there should be virtually nothing left because it complicates the way we record everything. So, if someone takes out a $1000 loan and subsequently selects the USDT: ETH pool, the entire $1,000 must be added as liquidity to this USDT: ETH pool.

Based on the problem statement above, we concluded that the following should provide us with what we seek.

get\_amount\_out(x) = quote(1000 - x) \[JediSwap functions]

Opening this up results in a quadratic equation for x which then needs to be solved.

We’ve referred to the implementation from JediSwap’s Zapper contract \[[Link to the page](https://github.com/mesh-finance/zapper-starknet/blob/initial_poc/contracts/Zapper.cairo)].



The equation must be tested under extreme values so as to validate that the solution doesn’t turn out either negative or complex.

$$(997*x) / ((reserveIn * 1000) + (997 * x)) + x = (1000-x)/reserveIn$$

From the equation, ‘x’ represents the swapped amount, thus defining that x is a non-negative real number.



Let’s generalize the equation:

997 → 99.7% of loan amount as the protocol takes 0.3% as fees

$$(0.997*loan*x) / ((reserveIn * loan) + (0.997*loan * x)) + x = (loan - x)/reserveIn$$



Readjusting the equation to the standard form would give:

$$0.997*loan*x^2 + [1.997*loan*reserveIn-0.997*loan^2]x - loan^2*reserveIn = 0$$

Here since the ‘c’ is negative, 4ac is always negative thus, it’s safe to say discriminant is non-negative i.e. roots are real.

Given the constraints, the roots won’t have the same sign that is both + or - \[c/a is negative → Roots have opposite signs]

Assumption: loan == 1000



*   Case 1: reserveIn == loan

    x = 618.55

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>



*   Case 2: ReserveIn(10b) >>> loan

    x = 500.75



From a practical relational value from reserveIn, the loan amount has been taken from 0 to reserveIn and represented through GIF.

Here, the **black line shows the loan\_amount, red graph is our equation** and it can be seen that x (at y=0) doesn’t cross loan\_amount.

{% embed url="https://i.ibb.co/kXxwtNN/Automated-Liquidity-Provision.gif" %}
