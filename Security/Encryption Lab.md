# Data Protection Using Encryption

Lab overview
Cryptography is the conversion of communicated information into secret code that keeps the information confidential and private. 
Functions include authentication, data integrity, and nonrepudiation. 
The central function of cryptography is encryption, which transforms data into an unreadable form.

Encryption ensures privacy by keeping the information hidden from people who the information is not intended for. 
Decryption, the opposite of encryption, transforms encrypted data back into data; it won’t make any sense until it has been properly decrypted.

In this lab, you will connect to a file server that is hosted on an Amazon Elastic Compute Cloud (Amazon EC2) instance. 
You will configure the AWS Encryption command line interface (CLI) on the instance. 
You will create an encryption key by using the AWS Key Management Service (AWS KMS). 
The key will be used to encrypt and decrypt data. Next, you will create multiple text files that are unencrypted by default. 
You will then use the AWS KMS key to encrypt the files and view them while they are encrypted. 
You will finish the lab by decrypting the same files and viewing the contents.

## Objectives
Create an AWS KMS encryption key
Install the AWS Encryption CLI
Encrypt plaintext
Decrypt ciphertext


### Create an AWS KMS key

<img width="656" height="478" alt="image" src="https://github.com/user-attachments/assets/8b04b47b-5388-4024-9ca3-3d8252a8a963" />

<img width="632" height="442" alt="image" src="https://github.com/user-attachments/assets/acbfaeb7-8cd9-434c-9a2b-bc8b60ac0ba2" />


### Configure the File Server instance
<img width="744" height="511" alt="image" src="https://github.com/user-attachments/assets/aeb68ccc-0cca-48d9-9889-5d9d786cca1c" />


Now you will install the AWS Encryption CLI and export your path. 
By doing this, you will be able to run the commands to encrypt and decrypt data.

<img width="800" height="463" alt="image" src="https://github.com/user-attachments/assets/3d6d6dc3-cd94-421e-9f14-bb2f1748cf8b" />

<img width="904" height="614" alt="image" src="https://github.com/user-attachments/assets/10de40be-65f7-4664-b97e-710893fb8dd3" />

<img width="709" height="497" alt="image" src="https://github.com/user-attachments/assets/d82e55ee-5d39-4611-a4c0-8c6a0ebf62b6" />



### Encrypt and decrypt data

In this task, you will create a text file with mock sensitive data in it. 
You will then use encryption to secure the file contents. 
Then, you will decrypt the data and view the file contents

<img width="1214" height="490" alt="image" src="https://github.com/user-attachments/assets/2234bcde-6452-46e6-8add-1dc36ffa74ee" />

file encrypted successfully.

<img width="772" height="563" alt="image" src="https://github.com/user-attachments/assets/104eea19-bfad-444e-9a08-172820d41053" />


The encryption and decryption process takes data in plaintext, which is readable and understandable, and manipulates its form to create ciphertext, 
which is what you are now seeing.

When data has been transformed into ciphertext, 
the plaintext becomes inaccessible until it's decrypted

<img width="811" height="484" alt="image" src="https://github.com/user-attachments/assets/4c4a5154-64ff-4eff-a4ec-7019204a88f6" />


Next, you will decrypt the secret1.txt.encrypted file.

<img width="848" height="391" alt="image" src="https://github.com/user-attachments/assets/1d8bb982-c9f3-43b8-99f6-e6c293adfef5" />
