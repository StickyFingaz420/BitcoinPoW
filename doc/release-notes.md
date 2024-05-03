26.2.1 Release Notes (BTCW)
==================

Bitcoin Core version 26.2.1 is now available from:

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

Hardforked BTCW to require more cpus.

Addressed the following issue:
```
The growth of computers was too slow and allowed for too much hashrate per computing device.
```

Credits
=======

Thanks to everyone who directly contributed to this release:

- FluffyFunction

As well as to everyone that helped with translations on
[Transifex](https://www.transifex.com/bitcoin/bitcoin/).
