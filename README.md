# Usage
## `scripts/pentest/web/graphql/decode_burp_traffic/decode_burp_traffic.py`
The script decodes base64 encoded burp suite http history traffic. This can then be further used to extract certain graphql keywords and create a wordlist for the tool [clairvoyance](https://github.com/nikitastupin/clairvoyance).

1. Go through a website manually with Burp open and browser proxy setup
2. In Burp go to `Proxy->HTTP history->left click on anything and CTRL+A->Save Items` and save the file to where the script is located with name `traffic.xml`
3. Decode the captured traffic: `python3 decode_burp_traffic.py > decoded_traffic.log`
4. Extract words form the traffic that match the GraphQLs naming convention: `grep -o  '[_A-Za-z][_0-9A-Za-z]*'  decoded_traffic.log | sort -u > graphql-wordlist.txt`
5. The wordlist can now be used with [clairvoyance](https://github.com/nikitastupin/clairvoyance) in order to find more queries, mutation, fields, etc. for a better schema file.
