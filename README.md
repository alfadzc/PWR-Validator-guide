# PWR-Validator-guide
## Step by Step Guide to set up PWR Chain Validator
# ⚡ PWR Chain Validator Node 

Welcome to the PWR Chain inaugural testnet! This guide helps you set up a validator node

---

## 📋 Requirements

- **CPU:** 2 vCPU  
- **RAM:** 4 GB  
- **Disk:** 100 GB or higher  
- **Bandwidth:** 400Mbps (down), 800Mbps (up)  
- **Open Ports:**
  - TCP: 8231, 8085, 9864
  - UDP: 7621

## 🖥️ Setup on Ubuntu Server

## # Step 1: Update OS
```
sudo apt update && sudo apt-get upgrade -y
```

## # Step 2: Install Java
```
sudo apt install default-jdk -y
```
## # Step 3: Open Required Ports
#### # Using UFW (Uncomplicated Firewall):
```
sudo ufw allow 8231/tcp
sudo ufw allow 8085/tcp
sudo ufw allow 9864/tcp
sudo ufw allow 7621/udp
sudo ufw reload
```
#### # Using iptables:
```
sudo iptables -A INPUT -p tcp --dport 8231 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 8085 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 9864 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 7621 -j ACCEPT
sudo netfilter-persistent save
```
- ⚠️NOTE: On cloud providers, open ports in the firewall/security group too.
## # Step 4: Install Validator node software and config file
```
wget https://github.com/pwrlabs/PWR-Validator/releases/download/15.63.3/validator.jar
wget https://github.com/pwrlabs/PWR-Validator/raw/refs/heads/main/config.json
```
## # Step 5: Setup your password file
```
echo "your-password-here" > password
```
## # Step 6: Run PWR Node
- Replace <YOUR_SERVER_IP> with your server's actual IP.
```
nohup sudo java --enable-native-access=ALL-UNNAMED -jar validator.jar --ip <YOUR_SERVER_IP> --password password &
```
- ⚠️NOTE: Make sure ports 8085 and 8231 are open for TCP.
## # Step 7: 
- Get Your PWR Validator Address
```
java -jar validator.jar get-address password
```

## # Step 8: Become a Validator Node
- Join Discord: https://discord.gg/jGDMbhZt
- Register your Validator: https://docs.google.com/forms/d/1ImUgk8JaKCwJR-7xiBNaA8-mb604CYdSKJfMRHacA60/viewform?edit_requested=true&pli=1
- Initially, your node will synchronize with the blockchain but will not assume validator responsibilities until it possesses staked PWR Coins.
- To obtain sufficient PWR Coins for staking, apply to become a testnet validator. Once approved, you can use our discord bot to claim 100k PWR to stake.
- After claiming your coins, your node will initiate a transaction to enlist as a validator.
## # Step 9: Checking your nodes logs

- If you wish to check your nodes logs, you can do so using the following command:
```
tail -n 1000 nohup.out -f
```
## 🌐 Check your Validator on PWR Chain Explorer: https://explorer.pwrlabs.io

## ✨Congratulations, you've now set up and run a PWR Chain validator node!


# #FAGs

## # 🗝 Check / Export PrivateKey
```
java -jar validator.jar get-seed-phrase password
```

## 🔄 Importing an Existing Wallet
- To import your old wallet using this update
- Replace <YOUR_PASSWORD> <SEED_PHRASE> with your password and seed-phrase
```
java -jar validator.jar import-seed-phrase <YOUR_PASSWORD> <SEED_PHRASE>
```
- Example:
```
java -jar validator.jar import-seed-phrase password public neither spoon scare diagram knife fragile road kit guess crucial batch
```





























