
# connect to VM 
sudo ssh -i /mnt/c/Users/harry/.ssh/id_rsa harry@104.199.130.206

# remote ssh can only read windows path like C:\Users\harry\.ssh\id_rsa

# if need to use "sudo ssh -F /mnt/c/Users/harry/.ssh/config de-zoomcamp" in WSL, then IdentityFile should be /mnt/c/Users/harry/.ssh/id_rsa

# docker-without-sudo
https://github.com/sindresorhus/guides/blob/main/docker-without-sudo.md

# download docker compose
wget https://github.com/docker/compose/releases/download/v2.32.4/docker-compose-linux-x86_64 -O docker-compose

chmod +x docker-compose 

./docker-compose 


# install Anaconda3
wget https://repo.anaconda.com/archive/Anaconda3-2024.10-1-Linux-x86_64.sh

nano ~/.bashrc
export PATH="$HOME/anaconda3/bin:$PATH"
source ~/.bashrc

# install pgcli
conda install -c conda-forge pgcli 

pip install -U pgcli

# connect to pgcli
pgcli -h localhost -U root -d ny_taxi 

pgcli -h localhost -p 5432 -U root -d ny_taxi 

# download csv
wget https://github.com/DataTalksClub/nyc-tlc-data/releases/download/yellow/yellow_tripdata_2021-01.csv.gz

gunzip yellow_tripdata_2021-01.csv.gz


# SFTP (SSH File Transfer Protocol) is a secure method for transferring files between local and remote computers.
sftp -i /mnt/c/Users/harry/.ssh/id_rsa harry@104.199.130.206
