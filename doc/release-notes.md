26.4.1 Release Notes (BTCW)
==================

Bitcoin PoW Core version 26.4.1 is now available from:

  <https://github.com/bitcoin-pow/BitcoinPoW/releases>

This release includes new bug fixes.

Please report bugs using the issue tracker at GitHub:

  <https://github.com/bitcoin-pow/BitcoinPoW/issues>

To receive security and update notifications, please subscribe to:

  <https://bitcoincore.org/en/list/announcements/join/>

How to Upgrade
==============

If you are running an older version, shut it down. Wait until it has completely
shut down (which might take a few minutes in some cases), then run the
installer (on Windows) or just copy over `/Applications/Bitcoin-pow-Qt` (on macOS)
or `bitcoin-powd`/`bitcoin-pow-qt` (on Linux).

Upgrading directly from a version of Bitcoin Core that has reached its EOL is
possible, but it might take some time if the data directory needs to be migrated. Old
wallet versions of Bitcoin Core are generally supported.

Compatibility
==============

Bitcoin Core is supported and extensively tested on operating systems
using the Linux kernel, macOS 11.0+, and Windows 7 and newer.  Bitcoin
Core should also work on most other Unix-like systems but is not as
frequently tested on them.  It is not recommended to use Bitcoin Core on
unsupported systems.

Notable changes
===============

Hardforked BTCW to prevent miningpools from existing.

https://github.com/bitcoin-pow/BitcoinPoW/pull/53

Addressed the following issue:
```
Since the mining loop was never signed, it was possible for a mining pool to write its own software such 
that it communicates with its users to do a majority of the mining work and then submits back to the pool
owner for the final block signature before block submission. To prevent this from occurring, a new
mining algorithm was created. The algorithm is a two step approach as follows:

1) Mining using utxos just as legacy mining.

2) Mine using a new 64 bit nonce and combine with the block signature to create some mud. Throw the mud thru
   a sha256 hash function and check if the hash meets a new threshold.


The validator will check to make sure that the signature in (1) matches the signature in (2) that was used
to sign the work and that both parts meet the thresholds for acceptance. Since the signatures must match,
the private key must be shared between (1) and (2). Sharing private keys will eliminate mining pools because all
trust is now lost.

The other attempt at pool formation will be to have the users only perform (1) and then send back to the pool for the
pool to finish doing (2). This will fail because the amount of work to do (1) is about 1% of the total work and the
remaining 99% of the work is in (2). This means that users would send work back to the pool and sit idle for 99% of 
the block time on average waiting for new work. Users have no benefit of using a pool and the pool will not form,
it they do form, they will be very unhealty pools that do not offer benefit to the users nor the pool owner.
```

Credits
=======

Thanks to everyone who directly contributed to this release:

- FluffyFunction

As well as to everyone that helped with translations on
[Transifex](https://www.transifex.com/bitcoin/bitcoin/).
