26.4.4 Release Notes (BTCW)
==================

Bitcoin PoW Core version 26.4.4 is now available from:

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
Updates have been made to show the stage1 and stage2 hashes per second using the rpc command 'getmininginfo'

You can look at the 'daystofind' field to get an estimate of how often you should mine a block on average.
You can determine which stage you are mining by looking at:

local-stage1-hashps and local-stage2-hashps

When they are 0 they are NOT active, when they non-zero they are active. Only one of them will be active at a given time.
cpuloading option has been removed since miningthreads can be used for overall cpu loading. Each active thread will be near 100% load.

cpuloadingpercent only shows for stage1 and shows correct value now.
When local-stage1-hashps: 0
CPU loading should show about 0%

getmininginfo transition from stage1 to stage2 was looking at uninitialized hashps data for many seconds before correct data was there. 
The result of this issue would have a divide by zero error and show 'The string inf is not a valid json number' when calling getmininginfo. 
This has been fixed.

Pull requests resolved in this release:
https://github.com/bitcoin-pow/BitcoinPoW/issues/61 - Mining status error
https://github.com/bitcoin-pow/BitcoinPoW/issues/62 - CPU loading shows 100% with low number of utxos

```

Credits
=======

Thanks to everyone who directly contributed to this release:

- FluffyFunction

As well as to everyone that helped with translations on
[Transifex](https://www.transifex.com/bitcoin/bitcoin/).
