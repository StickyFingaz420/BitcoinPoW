Bitcoin PoW Core integration/staging tree
=====================================

https://www.bitcoin-pow.org

https://www.twitter.com/bitcoin_pow

What is Bitcoin PoW?
----------------
BitcoinPoW is Bitcoin using proof of work(PoW) and proof of transactions (PoT) to verify blocks.


Combining PoW and PoT results in a highly mining distributed system where every wallet is forced to solo mine. 
----------------

Satoshi's original Bitcoin has become very mining centralized. One of the longest active BTC developers
(Luke Dashjr) has recently posted his worry on his new mining pool site www.ocean.xyz


 Message from Luke:
"Bitcoin is no longer censorship-resistant, and mining centralisation endangers its security too. It's time to fix that."

The reality is that his mining pool site will not fix the problem. The solution to the problem is to bring
mining back to the wallets and not the centralized ASIC farms. This would give a one to one vote, one node, one vote.

Combining PoW and PoT is an innovative approach which has never been done before.

Here is a look at a PoS equation that determines if a block meets its work threshold for acceptance:
```
hash(nStakeModifier + blockFrom.nTime + txPrev.vout.hash + txPrev.vout.n + nTime) < bnTarget * nWeight
```
This equation exists in a few PoS coins. The intention of this equation was to eliminate any way that a PoW system can 
modify any of the variables in a fast manner.

```
1 - nStakeModifier: This is block[n-1] and block[n-2] transaction hashes added together. These are the transactions that won the PoS in the past.
    This is defined and can't be manipulated.
2 - blockFrom.nTime: Time from block[n-1]. This is defined and can't be manipulated.
3 - nTime: Time for current block. This can be updated to help solve the equation, however there isn't much of a range as blocks are
    on average 10 minutes apart.
4 - txPrev.vout.hash: This is the previous hash of the current transaction candidate.  
5 - txPrev.vout.n: This is the vout number of the previous hash of the current transaction candidate. 
```

What biases the above equation is the term 'nWeight'. The more value in coin that was staked, the easier it is to solve
the equation.

BitcoinPoW using the PoW/PoT method eliminates this biased term 'nWeight'. This allows all staked transactions to have an
equal chance at solving the above equation. This is how the term PoS really turns into PoT. When all staked amounts are ignored,
they are really all just treated the same, thus PoT.

Looking at bullet #4 above, txPrev.vout.hash, a PoS system doesn't benefit from solving the equation regardless of the number of transactions because
if there is just one transaction, it is heavily weight by the amount in that transaction. If there are many transactions, there is a greater variation
in hashes to help solve the equation, but each transaction is reduced because the weight is smaller.

By elimanating the term 'nWeight', PoW/PoT method forces the above equation to turn into PoW. A miner can increase the number of transactions to
generate a large set of hashes from which it can iterate thru to help speed up finding a solution. The larger the set and the faster the computer
can iterate thru, the higher the hash power. This is how the BitcoinPoW operates using PoW. Each transaction that is in the set, was a valid stake
at some time in the past, this is how it also uses PoT.



Benefit of combining PoW/PoT
----------------
Combining PoW/PoT has never been done before and offers some interesting outcomes.

Here are the two main requirements of BitcoinPoW:
```
1 - Requires PoW - Users must burn energy (CPU or ASIC) to solve the PoW equation.
2 - Requires PoT - Users must stake at least 1 satoshi so that a transaction is valid in the PoW equation. Amount of coin does not matter, it is wise 
    to spend as little as possible when creating a transaction.
```


Here are the benefits:
```
1 - Prevents pools from forming. Very decentralized mining naturally happens.
2 - All users will naturally solo mine.
```


Naturally prevents pools from forming
----------------

Having a one node one vote system is ideal. BitcoinPoW has found the solution to turn Bitcoin into a fully decentralized mining system. Let's take a look how.

Pools are always created to make it easier for users to get at least some of the block reward. Solo mining is so incredibly difficult in Bitcoin that most don't attempt
because they will never find a block in their lifetime, so they join a pool instead. The PoW method in Bitcoin allows for this to happen. Templates are created
and all the miners get the templates and periodically submit work back to the pool to prove they are trying to solve the difficult equation. When the pool node
gets a block back that meets the difficulty, it submits to the Bitcoin network.

Let's attempt to create a pool for BitcoinPoW (uses PoW/PoT)
----------------

Lets dummy down the PoW equation to what really matters:
```
hash(previous_stake_hash + others) < bnTarget
```

At a basic level, the miner must iterate thru all of its previous stake hashes to try and solve the equation. 

If the coin was a proof of stake, the user could simple send their coin to a pool and the pool would pay them back a percentage of what they gave. 
BitcoinPoW is not a PoS coin. Having more coin does not let a miner find a solution any faster. Holding 1 Million BitcoinPoW (BTCW) wouldn't find a 
block any faster than holding 0.00000001 BTCW, thus a PoS pool won't work. 

If the coin was a proof of work, the user could send all their previous staked transactions to the pool, the pool could take them and send them to miners with more power to hash them faster. However, the problem
comes once it is time to apply the BlockSignature to the BitcoinPoW block. The pool would have to send the block to the user who submitted the winning transaction because they are
the only one that can sign it with the key for the block reward. If the pool sends the block to the user for signing, anyone who submits at that point will be submitting a 
block in which the payment goes directly to the user. Would a user want to be honest and give the pool coin back after the user received his reward???

Pools can't logically form using PoW/PoT, thus BitcoinPoW will naturally have all node operators solo mining. This will create a huge decentralized mining network.

Bitcoin miners never have to sign information, thus BTC can form large centralized mining pools. All the signing happens using the pool operator's wallet. BitcoinPoW is the
solution to the problem.


Are there benefits to owning more coin?
----------------

Obviously in a PoS coin the more coin you own the more block rewards you'll get. With BitcoinPoW, the PoW/PoT relies on a large number of transactions and 
the speed at which a CPU or ASIC can crunch thru them. Having more transactions is required to mine more blocks, however at some point, there will be too many
transactions and not enough PoW power. Once you have exceeded the power of your mining machine, having more transactions does not help you. There is a variable
of time that increments every seconds and that adds continued varaition to the transaction hashes. Having real mining hardware like a CPU is essential to mining
more blocks. In fact, when a miner gets maxed out, it is time to run parallel wallets to distribute the power across the CPU cores and threads.

The minimum cost of a transaction is 1 satoshi. Even if we decide to pay 0.00001 per transaction and we have 1 BTCW, how many transactions can we create?
1/0.00001 = 100,000 transactions. At the time of writing this, I'm observing about 30% single core loading with about 10,000 transactions per wallet.
This means I can mine with about 10 wallets comfortably on my computer using 1 BTCW. Using 0.00001 fees, 1 BTCW gives about 1 computer's worth of PoW. There is
an advantage to owning more BTCW if you buy the required hardware to mine the transactions.

We should note that at some point in the future, transaction cost will rise. Imagine users trying to allocate block space for transactions at the same time
users are trying to send BTCW to others. This will create competition to use the block space. The cost to mine more blocks will increase. This is similar
to how the cost to mine more on BTC always costs more as well. 

Even though the number of transactions is limited to:
```
21 Million / 0.00000001 = 2.1 8 10^15 transaction hashes
```
The total hashpower is not limited because CPU, eventually ASIC speed will keep increasing. Once the hardware speed overcomes all the possible hashes that can be created, then BitcoinPoW will have reached
its peak hashpower. This isn't a problem though because nobody can mine faster to attack it anyway once the max limit is reached. By the time the max limited is reached, the BitcoinPoW network will be
massive in nodes and massive in mining decentralization.


How to mine
-------
Goals of mining are simple. Create as many transactions for your mining needs. You can also create more transaction as a reserve for the future(HINT HINT). 
As a simple rule from above, we have established 1 BTCW gives about 1 computer's worth of PoW. Look below on how to get free BTCW to start mining.

Below is a Python script that can be used to help generate transaction. I generally like to fill about 10,000 
transactions per BTC address.

main.py
```
from bitcoinrpc.authproxy import AuthServiceProxy, JSONRPCException
from pprint import pprint
import time
import re

if __name__ == '__main__':

    # rpc_user and rpc_password are set in the bitcoin-pow.conf file
    rpc_user = "PUT_YOUR_USER_HERE"
    rpc_pass = "PUT_YOUR_PASS_HERE"
    rpc_host = "127.0.0.1"

    prevHeight = 0
    block_count = 0
    while 1:

        rpc_connection = AuthServiceProxy(f"http://{rpc_user}:{rpc_pass}@{rpc_host}:9332", timeout=240)

        commands = [["getblockcount"]]
        height = rpc_connection.batch_(commands)
        if prevHeight != height[0]:
            prevHeight = height[0]
            print(height[0])
            
            block_count = block_count + 1
            
            if block_count > 25:
                break            
               
            while 1:
                txid = rpc_connection.sendtoaddress('PUT YOUR LEGACY BTC ADDRESS STARTING WITH A 1 HERE', 0.00001)  
                print(txid)  
                
                try:
                    # At some point, we will send and tx will not hit mem pool and we need to abandon tx to get balance back.
                    # keep doing this to keep it simple. It only abandons if it needs to.
                    commands = [["abandontransaction", txid]]                    
                    resp = rpc_connection.batch_(commands)                       
                except Exception as err:
                        # this is good, keep sending txs
                    continue

                print("abandontransaction was successful")    
                break # abandontransaction happened, we are done till next block
                    
                time.sleep(60)


```

setup.py
```
#!/usr/bin/env python

from distutils.core import setup

setup(
    name='python-bitcoinrpc',
    version='1.0',
    description='Enhanced version of python-jsonrpc for use with Bitcoin',
    long_description=open('README.rst').read(),
    author='Jeff Garzik',
    author_email='<jgarzik@pobox.com>',
    maintainer='Jeff Garzik',
    maintainer_email='<jgarzik@pobox.com>',
    url='http://www.github.com/jgarzik/python-bitcoinrpc',
    packages=['bitcoinrpc'],
    classifiers=[
        'License :: OSI Approved :: GNU Library or Lesser General Public License (LGPL)', 'Operating System :: OS Independent'
    ]
)

```

start_btcw.sh   script to help start 2 wallets
```
./bitcoin-pow-qt &
./bitcoin-pow-qt --listen=0 --datadir=/home/software/.btcw1 &
```

bitcoin-pow.conf
```
rpcuser=PUT_YOUR_USER_HERE
rpcpassword=PUT_YOUR_PASS_HERE
rpcallowip=127.0.0.1
rpcport=9332
server=1
listen=1
addresstype=legacy
```


Steps
```
 0 - Copy main.py and setup.py from above and run:  python setup.py install
 1 - Download QT wallet from www.bitcoin-pow.org    Linux or Windows
 2 - Create directory /home/software/.btcw1   or whatever you'd like to store the data directory for the SINK wallet
 3 - Run the start_btcw.sh script
 4 - Create a SOURCE wallet for the above Python script to rpc connect to and issue commands to create transactions.
     This will use the default .bitcoin-pow directory
 5 - Create a new SINK wallet(do not copy SOURCE wallet). This will use another data location such as
     /home/software/.btcw1
 6 - Using SOURCE wallet, go to settings->Options->"Open Configuration File"    Put bitcoin.conf file contents there and save.
 7 - Close both wallets.
 8 - Run the start_btcw.sh script again
 9 - Modify main.py with your username/pass and legacy BTC address to send transactions to. Address must start with a '1'.
10 - Run the python script to generate transactions:  python main.py
```

When your wallet starts getting loaded around 40%, you might want to create a new wallet with a new wallet.dat and generate
a new BTC address in the python script and create transactions again.


CPU or ASIC?
-------
Everything can be turned into an ASIC. An ASIC is just a way to speed operations up. Part of the BitcoinPoW algorithm could be
placed inside an ASIC in the future, however the purpose of BitcoinPoW is to create a version of Bitcoin that cannot form
pools. Read above on how BitcoinPoW prevents pools. For now, all mining is CPU mining on BitcoinPoW. It would take years for someone
ready to invest and design the ASIC to do so. Even if/when ASICS come, the true benefit of BitcoinPoW is its PoW/PoT forcing
solo mining decentralization.


Free coins
-------
If you would like to start mining you can get coins from an exchange or find some free satoshis on twitter: @bitcoin_pow


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
