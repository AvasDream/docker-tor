## Usage

`docker build . -t tor`

`docker run --rm -p 5901:5901 -p 6901:6901 tor`

Log in on Browser at ```

Get new gpg keys

`gpg --homedir "$HOME/.local/share/torbrowser/gnupg_homedir/" --refresh-keys --keyserver pgp.mit.edu keyserver.ubuntu.com pool.sks-keyservers.net`


## Sources 


https://github.com/ConSol/docker-headless-vnc-container 




```
RUN apt install apt-transport-https curl software-properties-common -y &&\
    add-apt-repository universe &&\
    apt update &&\
    apt install torbrowser-launcher -y 

---

RUN echo "deb https://deb.torproject.org/torproject.org xenial main" >> /etc/apt/sources.list &&\
    echo "deb-src https://deb.torproject.org/torproject.org xenial main" >> /etc/apt/sources.list &&\
    apt install apt-transport-https curl -y &&\
    curl https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --import &&\
    gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | apt-key add - &&\
    apt update &&\
    apt install tor deb.torproject.org-keyring -y 

---

RUN echo "deb https://deb.torproject.org/torproject.org xenial main" >> /etc/apt/sources.list &&\
    echo "deb-src https://deb.torproject.org/torproject.org xenial main" >> /etc/apt/sources.list &&\
    apt install apt-transport-https curl software-properties-common -y &&\
    curl https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --import &&\
    gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | apt-key add - &&\
    add-apt-repository ppa:micahflee/ppa &&\
    apt update &&\
    apt install torbrowser-launcher -y 
```