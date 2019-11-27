# TorShare

TorShare enables file sharing between two parties over Tor.

### Design

TorShare needs a relay server which just relays information between two parties. The relay server can't see the data being relayed since the data is encrypted using a shared key agreed between two parties.

The sender starts a Tor hidden service for the file which needs to be transmitted and the address is sent to the receiver using the relay server. The hidden node address and the file name to be received is encrypted using a password agreed between both sender and receiver. 

When the sender starts the hidden node and sends the info the relay, the relay will return a channel name of 6 chars. The receiver needs to know both the password and the channel name to receive the file.

The relay shouldn't be able to figure out anything related to the transfer. Since the file transfer is also done over the Tor network, the transfer is encrypted as well.

Once the transfer is completed, the receiver will send a message directly to sender and sender will teardown the Tor hidden service.