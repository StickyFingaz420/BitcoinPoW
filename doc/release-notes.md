26.4.6 Release Notes (BTCW)
==================

Bitcoin PoW Core version 26.4.6 is now available from:

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
When the argument 'automine' is set to one, the wallet should start mining when started using the active wallet.
./bitcoin-pow-qt -automine=1
Default behavior is to NOT mine.

Mining status shows correctly.

Number of utxos are always shown regardless if mining or not.

Pull requests resolved in this release:
https://github.com/bitcoin-pow/BitcoinPoW/issues/67 - sequentially consistent memory operations across status is needed #67
https://github.com/bitcoin-pow/BitcoinPoW/issues/68 - Number of utxos should always show
https://github.com/bitcoin-pow/BitcoinPoW/issues/69 - Add automine argument


```

Credits
=======

Thanks to everyone who directly contributed to this release:

- FluffyFunction

As well as to everyone that helped with translations on
[Transifex](https://www.transifex.com/bitcoin/bitcoin/).
