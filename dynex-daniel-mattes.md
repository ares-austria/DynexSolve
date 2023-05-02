# How to find reference to Daniel Mattes in the Dynex code?

Dynex is a crypto project that makes fantastical claims. It is healthy to be skeptical in this field. It has been claimed by
<a href="https://www.youtube.com/watch?v=VecEvumSRts">multiple</a> <a href="https://twitter.com/ScamPatrol12/status/1626088064698441728">sources</a>
that Dynex is a scam orchestrated by Daniel Mattes, a character with <a href="https://www.reuters.com/article/us-sec-jumio-mattes-idUSKCN1RE260">a questionable past</a>.

The key point about the DynexSolve algorithm that promises to beat everything out there is the idea of Neuromorphic computing. Nice, but does it hold water?
The secret sauce here is the software that is supposed to be doing that computation is not open. When examining it closely it seems like it has some
references to common hash functions BLAKE256 and Slow-Hash from Monero. 

In addition the proprietary code has references to a Linux user whose home directory is `/home/daniel`. Could this be Daniel Mattes? We don't know, but
it seems like an unlikely coincidence given the speculation about Mattes' involvement in the project. Is this the smoking gun linkin Daniel and Dynex?
We invite the Dynex team to explain this and we will correct if we are wrong.

The reference to the Linux user `daniel` is in the official repository of Dynex. In the miner repository there are two closed source binary files.
They contain the reference to developer Daniel as shown in the hex-dump screenshots at the end of this document. But do not take our word for it.
Look for yourself with the following steps:

1. Download the two closed libraries from the official repository of DynexSolve:
   - https://github.com/dynexcoin/DynexSolve/raw/main/Crypto.tar.xz
   - https://github.com/dynexcoin/DynexSolve/raw/main/libCrypto.tar.xz
2. The two files are compressed with XZ. Extract the two files to get the uncompressed binaries.
3. Open the files in a hex editor - for example the online https://hexed.it/
4. Search for "daniel" in the hex dump
5. Draw your own conclusions

![Daniel Mattes behind DynexSolve](https://i.imgur.com/V0hb2mt.gif)
