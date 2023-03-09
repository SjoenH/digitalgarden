---
{"dg-publish":true,"permalink":"/vault-one/articles/how-to-use-git-secret-and-handle-gpg-keys-securely-on-multiple-machines/"}
---


**How to Use Git-Secret and Handle GPG Keys Securely on Multiple Machines**

Git-secret is a useful tool that allows you to store private files and information inside a git repository. In this post, we’ll cover the basics of using git-secret and provide tips for handling gpg keys securely on multiple machines.

**Using Git-Secret**

To get started with git-secret, you’ll need to have `gpg` and `git-secret` installed on your machine. Once you have these tools installed, follow these steps to use git-secret:

1.  **Initialize git-secret:** Navigate to your git repository and run `git secret init` to initialize git-secret.
2.  **Import public keys:** Before adding trusted users, make sure you have their public keys in your gpg keyring. You can do this by asking them to send you their public key and then importing it using `gpg --import filename`.
3.  **Add trusted users:** Run `git secret tell email@address.id` to add the email addresses of the users you trust. These users will be able to encrypt and decrypt files using their personal secret key.
4.  **Encrypt files:** To encrypt a file, run `git secret add filename`. This will encrypt the file and add it to the repository.
5.  **Decrypt files:** To decrypt encrypted files in the repository, run `git secret reveal`.

**GPG Keys**

Follow the GitHub guide
[Generating a new GPG key - GitHub Docs](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)


**Handling GPG Keys Securely on Multiple Machines**

If you need to use your gpg key on multiple machines, you can do so by exporting your private key from one machine and importing it on the others. Here’s how:

1.  **Export your private key:** On the machine where your private key is currently stored, run `gpg --export-secret-keys` to export your private key.
2.  **Transfer your private key:** Transfer the private key file to the other machines using a secure method such as a USB drive or a secure file transfer protocol.
3.  **Import your private key:** On each machine where you want to use your gpg key, run `gpg --import` to import your private key.

By following these steps, you can use git-secret and handle gpg keys securely on multiple machines.