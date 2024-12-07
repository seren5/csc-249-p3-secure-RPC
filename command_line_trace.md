# Command Line Trace
## Certificate Authority
Certificate Authority started using public key '(45995, 56533)' and private key '10538'
Certificate authority starting - listening for connections at IP 127.0.0.1 and port 55553
Connected established with ('127.0.0.1', 53498)
Received client message: 'b'$127.0.0.1:65432:(18391, 56533)'' [31 bytes]
Signing '127.0.0.1:65432:(18391, 56533)' and returning it to the client.
Received client message: 'b'done'' [4 bytes]
('127.0.0.1', 53498) has closed the remote connection - listening 
Connected established with ('127.0.0.1', 53505)
Received client message: 'b'key'' [3 bytes]
Sending the certificate authority's public key (45995, 56533) to the client
Received client message: 'b'done'' [4 bytes]
('127.0.0.1', 53505) has closed the remote connection - listening 

## Secure Server
Generated public key '(18391, 56533)' and private key '38142'
Connecting to the certificate authority at IP 127.0.0.1 and port 55553
Prepared the formatted unsigned certificate '127.0.0.1:65432:(18391, 56533)'
Connection established, sending certificate '127.0.0.1:65432:(18391, 56533)' to the certificate authority to be signed
Received signed certificate 'D_(10538, 56533)[127.0.0.1:65432:(18391, 56533)]' from the certificate authority
server starting - listening for connections at IP 127.0.0.1 and port 65432
Connected established with ('127.0.0.1', 53507)
Received request for TLS handshake from client
Sending signed certificate D_(10538, 56533)[127.0.0.1:65432:(18391, 56533)] to the client
Receiving an encrypted symmetric key from the client
TLS handshake complete: established symmetric key '15150', acknowledging to client
Received client message: 'b'HMAC_42541[symmetric_15150[Hello, world]]'' [41 bytes]
Decoded message 'Hello, world' from client
Responding 'Hello, world' to the client
Sending encoded response 'HMAC_42541[symmetric_15150[Hello, world]]' back to the client
server is done!

## VPN
VPN starting - listening for connections at IP 127.0.0.1 and port 55554
Connected established with ('127.0.0.1', 53506)
Received client message: 'b'127.0.0.1~IP~65432~port~TLS Handshake Request'' [45 bytes]
connecting to server at IP 127.0.0.1 and port 65432
server connection established, sending message 'TLS Handshake Request'
message sent to server, waiting for reply
Received server response: 'b'D_(10538, 56533)[127.0.0.1:65432:(18391, 56533)]'' [48 bytes], forwarding to client
Received client message: 'b'E_(18391, 56533)[15150]'' [23 bytes], forwarding to server
Received server response: 'b"symmetric_15150[Symmetric key '15150' received]"' [47 bytes], forwarding to client
Received client message: 'b'HMAC_42541[symmetric_15150[Hello, world]]'' [41 bytes], forwarding to server
Received server response: 'b'HMAC_42541[symmetric_15150[Hello, world]]'' [41 bytes], forwarding to client
VPN is done!

## Secure Client
Connecting to the certificate authority at IP 127.0.0.1 and port 55553
Connection established, requesting public key
Received public key (45995, 56533) from the certificate authority for verifying certificates
Client starting - connecting to VPN at IP 127.0.0.1 and port 55554
Verified Certificate.
The client is not verified to be communicating with the port and IP specified in the certificate
Generated symmetric key: 15150
Encrypted symmetric key: E_(18391, 56533)[15150]
Encrypted symmetric key sent to server.
TLS handshake complete: sent symmetric key '15150', waiting for acknowledgement
Received acknowledgement 'Symmetric key '15150' received', preparing to send message
Sending message 'HMAC_42541[symmetric_15150[Hello, world]]' to the server
Message sent, waiting for reply
Received raw response: 'b'HMAC_42541[symmetric_15150[Hello, world]]'' [41 bytes]
Decoded message 'Hello, world' from server
client is done!