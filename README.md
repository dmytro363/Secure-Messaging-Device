# Secure USB Messenger

## Description
Secure USB Messenger is a hardware USB device designed for secure transmission of confidential messages between users over the internet. The system operates independently of the host computer’s network and provides end-to-end encrypted messaging using dedicated hardware.

## Hardware Components
- **Arduino Pro Micro** — handles USB communication with the host computer.
- **ESP-12F (ESP8266)** — provides Wi-Fi connectivity and manages message transmission.

## Security
- **AES (GCM mode)** — encrypts messages.
- **SHA-256** — used for key derivation if needed.
- **Asymmetric encryption (RSA/ECC)** — for secure transmission of symmetric keys between devices.
- All messages are encrypted before sending.
- A unique nonce is used for each message.
- Authentication tags ensure message integrity.
- Messages are never transmitted in plaintext.

## Operation

### Sending a message
1. The user inputs a message via the host computer.
2. The device generates a nonce and encrypts the message using AES-GCM.
3. The symmetric key is transmitted to the receiving device using asymmetric encryption.
4. Transmitted data includes: nonce, ciphertext, authentication tag, and the encrypted symmetric key.

### Receiving a message
1. The device receives encrypted data.
2. The symmetric key is decrypted using the device’s private key.
3. The message is decrypted, and the authentication tag is verified.
4. The plaintext message is displayed to the user.

## Key Management
- Each device has an asymmetric key pair (private and public key).
- The public key of one device is used to securely transmit the symmetric key to the other device.
- The symmetric key is used to encrypt all messages.

## Project Status
- Active development.
- Type: Educational / Experimental Hardware Security Project.

## Author
Developed as an educational and experimental project in the fields of embedded systems, applied cryptography, and network communication.
