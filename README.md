Install node (Get the preinstall pack download the .zip package here https://github.com/Credit-Smartchain/preinstallserver )

Upload via SFTP preinstallnode.zip

Create mainnet folder and move preinstallnode.zip to this folder

$ mkdir mainnet

$ mv preinstallnode.zip ./mainnet/

$ cd mainnet

$ yum install zip unzip

$ unzip preinstallnode.zip


Create new account

$ ./geth --datadir=./mnode --password ./password.txt account new > account.txt

Copy address from account.txt

$ vi account.txt

paste the address somewhere : (ex: 0xC0ea77B1D07e5c384A2f1Ba7a8c01e38a6Ac48A0)

Init node

$ ./geth --datadir ./mnode init credit.json

Create Start.sh

Below you need to paste your wallet in between the ''  replacing the dummy text: PASTE YOUR WALLET YOU COPIED EARLIER HERE

$ vi start.sh

Copy and paste your wallet in between the ''  replacing the dummy text: PASTE YOUR WALLET YOU COPIED EARLIER HERE

nohup ./geth -snapshot=false --datadir mnode --syncmode 'full' --gcmode=archive --port 40605 --http --http.corsdomain='*' --http.port 3545 --http.api 'personal,eth,net,web3,personal,admin,miner,txpool,debug,clique' --bootnodes enode://63fbe749af72c08ebdcf2b3212878c1b0131ddeef5e942852151b05997fd367b74981ba087cfc3ad95294cc4b00a7a649f9f99d903423cbf475e340faa6166f1@157.245.142.184:0?discport=40606 --networkid 13308 -unlock 'PASTE YOUR WALLET YOU COPIED EARLIER HERE' --password ./password.txt --mine --allow-insecure-unlock 2>>chain.log &

Then copy the whole text and past into the start.sh file , write and quite

Run node

$ chmod +x start.sh

$ ./start.sh 

Check log

$ tail -f chain.log

