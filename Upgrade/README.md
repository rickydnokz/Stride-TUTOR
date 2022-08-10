# Chain upgrade to commit 15e65e9a364804671425051606fe0be6536452fe

Once the chain reaches the upgrade height, you will encounter the following panic error message:
`ERR UPGRADE "xxx" NEEDED at height: 155420`

```sudo systemctl stop strided
cd $HOME && rm -rf stride
git clone https://github.com/Stride-Labs/stride.git && cd stride
git checkout 15e65e9a364804671425051606fe0be6536452fe
make build
sudo cp $HOME/stride/build/strided /usr/local/bin
sudo systemctl restart strided && journalctl -fu strided -o cat
```

!!! DO NOT UPGRADE BEFORE CHAIN RECHES THE BLOCK `155420`!!!

# EXAMPLE
![alt text](https://github.com/rickydnokz/Stride-TUTOR/blob/main/Upgrade/step%201.png)
