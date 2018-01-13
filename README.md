# wcef-hackathon-2018
Guidelines for hackathon at WCEF 2018

# Background info about NuCypher

NuCypher is a key management system which leverages proxy re-encryption to control access over encrypted data.
You can find the white paper [here](https://cdn2.hubspot.net/hubfs/2807639/NuCypher%20KMS%20Technical%20White%20Paper.pdf?t=1510526466105) (although you don't have to read it all!).
If you have any questions, you can ask in person at the hackathon, or go to our [developer slack channel](https://nucypher-kms-slack.herokuapp.com/).

# Possible tasks for the hackathon

## Implementing proxy re-encryption library in languages other than Python or Javascript

We use split-key proxy re-encryption scheme. The reference implementation in its most readable, self-explaining form can be found [here](https://github.com/nucypher/nucypher-pre-python/blob/master/npre/umbral.py). In brief, encryption and decryption is just [ECIES](https://en.wikipedia.org/wiki/Integrated_Encryption_Scheme), but the ciphertext (or, more accurately, the ephemeral public key) can be transformed so that the data can be efficiently shared with more than one recepient via re-encryption.

Please check the [tutorial](https://blog.nucypher.com/proxy-re-encryption-playground-in-python-3bc66170b9bf) in order to set up the environment and play with re-encryption.

We need client libraries for the following languages: Go, Rust, C. If you wish to play with low-level cryptography in any of these languages (or even different ones if you like) - feel free to hack on this task.

## UI for mining node management console

Our mining nodes will be the workhorses of the network.
They stake the token and, instead of confirming transactions, they re-encrypt ciphertexts.
The mining process works in the following way:

* Miner deposits the token (must be greater than a set minimum amount);
* Miner locks the tokens for a specified time T (T >= 1 month);
* Mining itself occurs. The miner performs the required re-encryption during this period;
* The Miner now has three options. They can chose to reinvest block rewards back into mining, take profits, or commence a gradual spindown of their node in time T.

We also would like to see a visual graph so that the miner can compare how much tokens he gets over time if chosing different options.

The UI should be a web UI.
Could be built using any web tool (Python frameworks, nodejs frameworks, or whatever you love).

## UI for granting permissions
