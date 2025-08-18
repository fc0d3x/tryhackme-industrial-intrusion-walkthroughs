# TryHackMe - Cipher: AES-GCM Decryption Challenge

## Overview

This repository contains the solution to the "Cipher" challenge from TryHackMe, which focuses on analyzing encrypted telemetry traffic between a SCADA server and a pump controller. The challenge involves decrypting telemetry data using AES-GCM encryption and extracting a hidden sabotage command, which contains a flag.

## Challenge Breakdown

###Objective

The goal was to decrypt the second packet of telemetry traffic (cipher2.bin) and reveal the hidden sabotage command containing the flag. The data was encrypted using AES-GCM with a shared 16-byte nonce.

## Steps

#### Nmap Scan

Performed an Nmap scan to check for open ports and services on the target machine, revealing potential access points like HTTP, LDAP, and SMB.

#### Analyzing Encrypted Telemetry Packets

Two binary files (cipher1.bin and cipher2.bin) were provided, which contained the telemetry data. The telemetry data structure was as follows:

16-byte nonce

96-byte ciphertext

16-byte GCM tag

#### Decryption Process

The first packet (cipher1.bin) was decrypted using a known plaintext attack to extract the keystream.

The second packet (cipher2.bin) was then decrypted using the keystream obtained from the first packet.

#### Revealing the Flag

The decrypted second packet revealed the kill switch command and the flag: THM{Echo_Telemetry}.

## Tools and Techniques

Python: A Python script was used to automate the decryption process.

AES-GCM: The encryption method used in this challenge, leveraging both ciphertext and nonce for secure communication.