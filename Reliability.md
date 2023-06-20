# Reliability in Data Transfer

Let's assume we are sending message M from wallet A to wallet B. (A: sender, B: receiver).

Here M is in the form of a string. Let ‘x’ be the maximum message size that can be sent through WalletConnect.  x = 2000 bytes. 

Our message M can have a maximum size of 12kb (12 * 1024 bytes).

So, we need to break M into smaller chunks and send the message chunk-wise. Later at the receiver’s end, the original message should be reconstructed by merging all chunks together.
Each chunk should be associated with a unique identifier. 

Total number of chunks $(n) = \lceil\frac{M.size()}{x - 100}\rceil$

Here I am saving 100 bytes per chunk for its metadata, which would basically store its ID number. 