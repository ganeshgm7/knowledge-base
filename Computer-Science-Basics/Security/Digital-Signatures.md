# Digital Signatures

A digital signature is an electronic, cryptographic equivalent of a handwritten signature that provides a way to verify the authenticity and integrity of digital documents or messages. It uses public key infrastructure (PKI), which involves a pair of keys: a private key (kept secret by the signer) and a public key (shared openly).

## How Digital Signatures Work

1. **Document Hashing**: The content of the document is hashed, converting it into a fixed-length string of characters.
2. **Signature Creation**: The hash is then encrypted using the signer's private key, creating the digital signature.
3. **Attachment**: This digital signature is attached to the document.

### Verification Process

When the recipient receives the signed document, they can:

1. **Decrypt the Signature**: The signature is decrypted using the sender's public key.
2. **Rehash the Document**: The recipient hashes the received document again.
3. **Compare Hashes**: The decrypted hash and the newly generated hash are compared. If they match, the document is verified as authentic and unaltered.

## Real-time Example

Imagine you are applying for a loan online. You fill out the loan application form and sign it digitally. The digital signature ensures the following:

- **Authentication**: The bank knows the application genuinely came from you.
- **Integrity**: The application has not been altered since you signed it.
- **Non-repudiation**: You cannot deny signing the application later.

When the bank receives the application, they use your public key to verify your digital signature and proceed with processing your loan.

## Applications of Digital Signatures

- **Government**: E-filing of taxes and signing official documents.
- **Banking**: Authorizing transactions and signing loan agreements.
- **Legal**: Signing contracts and legal documents digitally.
- **E-commerce**: Authenticating transactions and online contracts.
- **Healthcare**: Securing patient records and prescriptions.

## Legal Framework in India

In India, digital signatures are legally recognized under the **Information Technology Act of 2000**. They are widely used in government services, such as e-filing income tax returns and Aadhaar authentication.

