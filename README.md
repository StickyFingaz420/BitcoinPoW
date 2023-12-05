Bitcoin PoW Core integration/staging tree
=====================================

https://www.bitcoin-pow.org

https://www.twitter.com/bitcoin_pow

What is Bitcoin PoW?
----------------
BitcoinPoW is Bitcoin mining via proof of work (using transactions) that can only be done on a CPU. ASICs cannot perform the algorithm any faster than
a normal computer running a full node.

Satoshi's original Bitcoin has become very mining centrazlied. One of the longest active BTC developers
(Luke Dashjr) has recently posted his worry on his new mining pool site www.ocean.xyz


 Message from Luke:
"Bitcoin is no longer censorship-resistant, and mining centralisation endangers its security too. It's time to fix that."

The reality is that his mining pool site will not fix the problem. The solution to the problem is to easliy bring
mining back to the wallet and not ASIC farms. This gives a one to one vote, one node, one vote.

The solution is an innovative approach which has never been done before.

The solution has found a way to prevent ASIC miners from mining PoW and make it only possible to mine using PoW
via a CPU.

Rather than perform low level repetetive work on rearranging bits and hashing to find so many leading zeros on a block hash,
BitcoinPoW performs work by using transactions. Users simply use their existing UTXOs and loop thru the following kernel
protocol until a solution is found:



BitcoinPoW kernel protocol
coinstake must meet hash target according to the protocol:
kernel (input 0) must meet the formula

```
hash(nStakeModifier + blockFrom.nTime + txPrev.vout.hash + txPrev.vout.n + nTime) < bnTarget
```
this ensures that the chance of mining a block is proportional to the amount of work that is done hashing transactions of coins one owns.
Keep in mind, the amount of coin that one owns does NOT make it any easier to find a block; it is the number of transactions
that determine how often one can find a block. The more transactions one has, the quicker they will most likely find a block.

Looking at the above equation,
nStakeModifier: scrambles computation to make it very difficult to precompute future proof-of-stake
blockFrom.nTime: slightly scrambles computation
txPrev.vout.hash: hash of txPrev, to reduce the chance of nodes generating coinstake at the same time
txPrev.vout.n: output number of txPrev, to reduce the chance of nodes generating coinstake at the same time
nTime: current timestamp, this can change once per second


ASICs cannot perform the loop any faster than a normal computer because each loop has such a strong dependence on the 
full node wallet apis and would be bottlenecked by this. Instead, a faster computer running a full node would have
an advantage looping though 1000 transactions per second and making the calculation above. A slower computer might run 100 transaction
calculations per second.

As more nodes come online, more proof of work using the transactions will make it nearly impossible to 51% attack. The benefit of
BitcoinPoW is that all a user needs to do is keep their full node wallet running and it automatically mines. There are about 4 main
BTC mining pools, with BitcoinPoW, you can't form pools because the work optimally is performed locally on the user's own wallet.
This will naturally grow the indepenent miners to a much larger number.

It can be noted that the proof of work using transactions, is actually a collapsed form of proof of stake. This means that a user
must actually own coins to make transactions, but the amount of coin can be near zero. A user with 10,000 coins would have the same
chance of finding a block as a user with 1 coin. This is because as they maximize the amount of transactions, 1 can make at least 
100,000 tiny transactions which is more than their computer can handle per second anyway. The developer initially mined 10 PoW
blocks to enable mining of valid transactions. BitcoinPoW coins are needed to mine, but the amount can be as small as 1 satoshi 
to mine.

Transactions are how the work is done. The amount of coin in the transaction, is meaningless. This is why I have coined the 
term "Collapsed Proof of Stake".

You can get coins from an exchange or find some free satoshis on twitter: @bitcoin_pow


For more information see https://www.bitcoin-pow.org

License
-------

Bitcoin PoW Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

Development Process
-------------------

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/fluffyfunction/BitcoinPoW/tags) are created
regularly to indicate new official, stable release versions of Bitcoin PoW Core.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md)
and useful hints for developers can be found in [doc/developer-notes.md](doc/developer-notes.md).

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/test), written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/test) are installed) with: `test/functional/test_runner.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and macOS, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.
