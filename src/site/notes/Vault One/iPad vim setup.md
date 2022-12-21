---
{"dg-publish":true,"permalink":"/vault-one/i-pad-vim-setup/"}
---


## Server
Debian server hosted at "servetheworld" for around 2 usd per month.
> Update. Seems like this server is too weak for development purposes. 

|SSD DISK | 	RAM |	CORE 	|TRAFIKK |	PRIS MND| Comment | 
|----------|-------|--------|--------|-------|---------|
|10 GB| 	512 MB |	1 core 	|Ubegrenset 	|19.50 kr|<- This is cheap, but might not be strong enough...|
|20 GB 	|1 GB 	|1 core 	|Ubegrenset 	|29.50 kr||
|40 GB 	|2 GB 	|2 core 	|Ubegrenset |	64.50 kr||
|80 GB 	|4 GB 	|4 core 	|Ubegrenset |	114.50 kr||
|160 GB 	|8 GB |	8 core 	|Ubegrenset| 	224.50 kr||
|240 GB 	|12 GB| 	8 core |	Ubegrenset |	298.50 kr||
|320 GB 	|16 GB |	8 core| 	Ubegrenset |	389.50 kr||

Sudo user is not setup. Let's create a user and add it to sudo-list.


## Mosh
### Client
On iOS, i use blink.sh.

### Server
Let's install Mosh on the server...
Problem, need to compile mosh since it does not support "true-colors" out of the box.

https://gist.github.com/kuntau/37698a5159ceac40982b1f7ae96b7db8#tldr
```bash
sudo apt install perl protobuf-compiler libprotobuf-dev \
libncurses5-dev zlib1g-dev libutempter-dev libssl-dev
git clone --depth=1 https://github.com/mobile-shell/mosh.git
cd mosh
./autogen.sh
./configure
make && sudo make install
```


## AstroNVim
Now we can install AstroNVim.

Problem, debian ships an out of date nvim and we need version 8.

Install version 8 from GitHub. -  [Link to v8 release page](https://github.com/neovim/neovim/releases/tag/v0.8.0)

```bash
wget https://github.com/neovim/neovim/releases/download/v0.8.0/nvim-linux64.deb
apt install nvim-linux64.deb
```

