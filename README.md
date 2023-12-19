# Namanda-install-node

Install a quick installation:    

    wget -q -O namada.sh https://api.nodes.guru/namada.sh && chmod +x namada.sh && sudo /bin/bash namada.sh

next step:

    source $HOME/.bash_profile

Create a user account:

    namada wallet address gen --alias my-account

Find Wallet

    namada wallet address find --alias my-account

Faucet token : https://faucet.heliax.click/


Check balance, if everything is okay go to the next step:

    namada client balance --token NAM --owner my-account

Initialising a validator account::

    namada client init-validator \
    --alias $VALIDATOR_ALIAS \
    --email $EMAIL \
    --account-keys my-account \
    --signing-keys my-account \
    --commission-rate 0.1 \
    --max-commission-rate-change 0.1

Bond token to your validator:

    namada client bond \
    --validator $VALIDATOR_ALIAS \
    --amount 999 \
    --source my-account

Check logs:

    journalctl -u namadad -f -o cat

Restart node:

    systemctl restart namadad

Check Syn

    curl -s localhost:26657/status | jq .result.sync_info.catching_up

Ports used:

    26656, 26657, 26658

Remove node:

    systemctl stop namadad
    systemctl disable namadad
    rm -rf ~/namada ~/.local/share/namada /etc/systemd/system/namadad.service

#Source_Guru node        
