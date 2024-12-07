# Text Document
This document includes:
- Overview of Application
- Format of an Unsigned Certificate
- Example Output
- A walkthrough of the steps of a TLS handshake (and what each step accomplishes)
- A description of two ways in which our simulation fails to achieve real security, and how these failues might be exploited by a malicious party
- Acknowledgments

## Overview of Application
This application is meant to establish a secure and encrypted channel between a client and a server, with a VPN in between. The client connects to the server, authenticates using asymmetric key pairs, and establishes a symmetric key for further communication.
This system includes a TLS handshake, a certificate authority to verify authenticity, and encryption withing cryptgraphy_simulator.py.

## Format of an Unsigned Certificate
The unsigned certificate contains a '$' for the certificate authority to read, then the server's ip, port, and a public key.
\${Server_IP}:{Server_Port}:{Public_Key} should be the format

## Example Output
Check command_line_trace.md

## Walkthrough
First, the client initiates the handshake by sending a message to the VPN, which forwards it to the server.
Then, the server generates a public/private key pair and an unsigned certificate, which it sends to the certificate authority to be signed.
After the certificate authority signs the certificate and sends it back to the serverm the server sends it to the client in the handshake.
The client receives the file and verifies the authenticity using the certificate authority's public key, and then extracts the server's information (IP, port, and public key).
The client then generates a symmetric key, encrypts it, and sends it to the server.
The server takes the symmetric key, decrypts it with its private key, and then uses it for communication between the client and server.
Messages aren't sent directly between the client and server, but go through the VPN.

## Description of Two Ways (Failure to achieve real security)
1. There was no verified certificate from a trusted certificate authority, and could result in fake certificates being generated to trick clients or servers while impersonating one end
2. The encryption/decryption system may be weak, and the generated keys aren't random, making it easier for attackers to make their way in

## Acknowledgments
I consulted with Tanya, who helped me think through the client, and Isabelle, who helped me think through the server. 