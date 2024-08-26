26.4.5 Release Notes (BTCW)
==================

Bitcoin PoW Core version 26.4.5 is now available from:

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
NEW COMMAND: You can now use just ONE wallet to create utxos and use as a normal wallet. Use the command `make_utxos`
shown below. You can send coin without using coin control. The logic has been adjusted so that when a user sends coin,
it will never pick a mining dust utxo transaction. No need to hassle with multiple send and receive wallets!!!


make_utxos number_utxos fee_rate

Create a specified number of utxos for the active wallet using the specified fee rate.
If total fee is high you may need to restart the wallet and user higher fee threshold: bitcoin-pow-qt.exe -maxtxfee=20.0
Requires wallet passphrase to be set with walletpassphrase call if wallet is encrypted.

Arguments:

    number_utxos (numeric or string, required) The number of utxos to create for the active wallet.
    fee_rate (numeric or string, required) Specify a fee rate in sat/vB.

Examples:

Create 1000 utxos with a fee of 20 satoshi/vB

    bitcoin-cli make_utxos 1000 20


Pull requests resolved in this release:
https://github.com/bitcoin-pow/BitcoinPoW/pull/65 - make_utxos command


```

Credits
=======

Thanks to everyone who directly contributed to this release:

- FluffyFunction

As well as to everyone that helped with translations on
[Transifex](https://www.transifex.com/bitcoin/bitcoin/).
