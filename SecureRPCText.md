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
