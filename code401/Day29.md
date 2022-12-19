# class 29
**PART 1:**
## Configuring Django Settings: Best Practices

### Managing Django Settings: Issues
  
- Different environments.

    Usually, you have several environments: local, dev, ci, qa, staging, production, etc. Each environment can have its own specific settings (for example: DEBUG = True, more verbose logging, additional apps, some mocked data, etc). You need an approach that allows you to keep all these Django setting configurations.

- Sensitive data.

    You have SECRET_KEY in each Django project. On top of this there can be DB passwords and tokens for third-party APIs like Amazon or Twitter. This data cannot be stored in VCS.

- Sharing settings between team members.

    You need a general approach to eliminate human error when working with the settings. For example, a developer may add a third-party app or some API integration and fail to add specific settings. On large (or even mid-size) projects, this can cause real issues.
- Django settings are a Python code.

    This is a curse and a blessing at the same time. It gives you a lot of flexibility, but can also be a problem – instead of key-value pairs, settings.py can have a very tricky logic.

### Setting Django Configurations: Different Approaches

There is no built-in universal way to configure Django settings without hardcoding them. But books, open-source and work projects provide a lot of recommendations and approaches on how to do it best. Let’s take a brief look at the most popular ones to examine their weaknesses and strengths.

- settings_local.py

    This is the oldest method. I used it when I was configuring a Django project on a production server for the first time. I saw a lot of people use it back in the day, and I still see it now.

    The basic idea of this method is to extend all environment-specific settings in the settings_local.py file, which is ignored by VCS.

#### Pros

1. Secrets not in VCS.

#### Cons

1. settings_local.py is not in VCS, so you can lose some of your Django environment settings.
2. The Django settings file is a Python code, so settings_local.py can have some non-obvious logic.
3. You need to have settings_local.example (in VCS) to share the default Django configurations for developers.

---
**PART 2:**
## What Is SSH: Understanding Encryption, Ports and Connection

### What Is SSH?

SSH, or Secure Shell Protocol, is a remote administration protocol that allows users to access, control, and modify their remote servers over the internet.

SSH service was created as a secure replacement for the unencrypted Telnet and uses cryptographic techniques to ensure that all communication to and from the remote server happens in an encrypted manner. It provides a mechanism for authenticating a remote user, transferring inputs from the client to the host, and relaying the output back to the client.

The example below shows a typical SSH prompt. Any Linux or macOS user can SSH into their remote server directly from the terminal window. Windows users can take advantage of SSH clients like Putty.  You can execute shell commands in the same manner as you would if you were physically operating the remote computer.

### How Does SSH Work

If you’re using Linux or Mac, then using SSH is very simple. If you use Windows, you will need to utilize an SSH client to open SSH connections. The most popular SSH client is PuTTY, which you can learn more about here.

For Mac and Linux users, head over to your terminal program and then follow the procedure below:

The SSH command consists of 3 distinct parts:

    ssh {user}@{host}

The SSH key command instructs your system that you want to open an encrypted Secure Shell Connection. {user} represents the account you want to access. For example, you may want to access the root user, which is basically synonymous with the system administrator with complete rights to modify anything on the system. {host} refers to the computer you want to access. This can be an IP Address (e.g. 244.235.23.19) or a domain name (e.g. www.xyzdomain.com).

When you hit enter, you will be prompted to enter the password for the requested account. When you type it in, nothing will appear on the screen, but your password is, in fact being transmitted. Once you’re done typing, hit enter once again. If your password is correct, you will be greeted with a remote terminal window.

### Understanding Different Encryption Techniques

Understanding Different Encryption Techniques
The significant advantage offered by SSH over its predecessors is the use of encryption to ensure a secure transfer of information between the host and the client. Host refers to the remote server you are trying to access, while the client is the computer you are using to access the host. There are three different encryption technologies used by SSH:

1. Symmetrical encryption
2. Asymmetrical encryption
3. Hashing

#### Symmetric Encryption

Symmetric encryption is a form of encryption where a secret key is used for both encryption and decryption of a message by both the client and the host. Effectively, anyone possessing the key can decrypt the message being transferred

Symmetrical encryption is often called shared key or shared secret encryption. There is usually only one key that is used, or sometimes a pair of keys, where one key can easily be calculated using the other key.

Symmetric keys are used to encrypt the entire communication during an SSH session. Both the client and the server derive the secret key using an agreed method, and the resultant key is never disclosed to any third party.

The process of creating a symmetric key is carried out by a key exchange algorithm. What makes this algorithm particularly secure is the fact that the key is never transmitted between the client and the host.

Instead, the two computers share public pieces of data and then manipulate it to independently calculate the secret key. Even if another machine captures the publically shared data, it won’t be able to calculate the key because the key exchange algorithm is not known.

It must be noted, however, that the secret token is specific to each SSH session, and is generated prior to client authentication. Once the key has been generated, all packets moving between the two machines must be encrypted by the private key. This includes the password typed into the console by the user, so credentials are always protected from network packet sniffers.

A variety of symmetrical encryption ciphers exist, including, but not limited to, AES (Advanced Encryption Standard), CAST128, Blowfish, etc. Before establishing a secured connection, the client and a host decide upon which cipher to use, by publishing a list of supported ciphers in order of preference. The most preferred cipher – from the clients supported ciphers – that is present on the host’s list is used as the bidirectional cipher.

For example, if two Ubuntu 14.04 LTS machines are communicating with each other over SSH, they will use aes128-ctr as their default cipher.

#### Asymmetric Encryption

Unlike symmetrical encryption, asymmetrical encryption uses two separate keys for encryption and decryption. These two keys are known as the public key and the private key. Together, both these keys form a public-private key pair.

A public key can be used by any individual to encrypt a message and can only be decrypted by the recipient who possesses their particular private key, and vice versa. These consist of extensive and seemingly random combinations of numbers and symbols, however, both public and private keys are paired using complex mathematical algorithms.

For example, in order to authenticate the sender, a message is encrypted using their own private key. Therefore, the message can only be decrypted using that specific sender’s public key. Note that both encryption and decryption mechanisms are automatic processes – you don’t need to do anything manually.

Unlike the general perception, asymmetrical encryption is not used to encrypt an entire SSH session. Instead, it is used during the key exchange algorithm of symmetric encryption. Before initiating a secured connection, both parties generate temporary public-private key pairs and share their respective private keys to produce the shared secret key.

Once a secured symmetric communication has been established, the server uses the client’s public key to generate and challenge and transmit it to the client for authentication. If the client can successfully decrypt the message, it means that it holds the private key required for the connection – the SSH session then begins.

#### Hashing

One-way hashing is another form of cryptography used in Secure Shell Connections. One-way-hash functions differ from the above two forms of encryption in the sense that they are never meant to be decrypted. They generate a unique value of a fixed length for each input that shows no clear trend which can be exploited. This makes them practically impossible to reverse.

It is easy to generate a cryptographic hash from a given input, but impossible to generate the input from the hash. This means that if a client holds the correct input, they can generate the cryptographic hash and compare its value to verify whether they possess the correct input.

SSH uses hashes to verify the authenticity of messages. This is done using HMACs, or Hash-based Message Authentication Codes. This ensures that the command received is not tampered with in any way.

While the symmetrical encryption algorithm is being selected, a suitable message authentication algorithm is also selected. This works in a similar way to how the cipher is selected, as explained in the symmetric encryption section.

Each message that is transmitted must contain a MAC, which is calculated using the symmetric key, packet sequence number, and the message contents. It is sent outside the symmetrically encrypted data as the concluding section of the communication packet.

### Authenticating the User

The final stage before the user is granted access to the server is authenticating his/her credentials. For this, most SSH users use a password. The user is asked to enter the username, followed by the password. These credentials securely pass through the symmetrically encrypted tunnel, so there is no chance of them being captured by a third party.

Although passwords are encrypted, it is still not recommended to use passwords for secure connections. This is because many bots can simply brute force easy or default passwords and gain access to your account. Instead, the recommended alternative is SSH Key Pairs.

These are a set of asymmetric keys used to authenticate the user without the need of inputting any password.
