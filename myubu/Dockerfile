# rolling is current
FROM ubuntu:rolling

# trusty is 14.x
#FROM ubuntu:trusty

# xenial is 16.x
#FROM ubuntu:xenial

# artful is 17.x
# FROM ubuntu:artful

LABEL description="Create a personal Ubuntu image"

# change root password
RUN echo "root:TODO-ROOT-PASSWD" | chpasswd

# update/upgrade/install system
RUN apt-get update; \
    apt-get upgrade -y; \
    apt-get install -y sudo vim curl iputils-ping fortune cowsay python3 git npm colossal-cave-adventure telnet man tmux htop caca-utils wget

# create user and setup sudo
RUN mkdir /home/TODO-UID; \
    groupadd -r dockeruser -g 433; \
    useradd -u 431 -r -g dockeruser -d /home/TODO-UID -s /bin/bash -c "Docker image user" TODO-UID; \
    chown -R TODO-UID:dockeruser /home/TODO-UID; \
    echo "TODO-UID:TODO-UID-PASSWD" | chpasswd; \
    echo "TODO-UID ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/TODO-UID && chmod 0440 /etc/sudoers.d/TODO-UID

# create .bashrc for the new user
RUN cp /root/.bashrc /home/TODO-UID; \
    echo "# Harris Overrides" >> /home/TODO-UID/.bashrc; \
    echo "alias ll='ls -alFp --color=never'" >> /home/TODO-UID/.bashrc; \
    echo "alias la='ls -Ap --color=never'" >> /home/TODO-UID/.bashrc; \
    echo "alias l='ls -CFp --color=never'" >> /home/TODO-UID/.bashrc; \
    echo "alias ls='ls -p --color=never'" >> /home/TODO-UID/.bashrc; \
    echo "alias grep='grep --color=never'" >> /home/TODO-UID/.bashrc; \
    echo "alias fgrep='fgrep --color=never'" >> /home/TODO-UID/.bashrc; \
    echo "alias egrep='egrep --color=never'" >> /home/TODO-UID/.bashrc; \
    echo "PS1='\w\$ '" >> /home/TODO-UID/.bashrc; \
    echo "alias h=history" >> /home/TODO-UID/.bashrc; \
    echo "alias cls=clear" >> /home/TODO-UID/.bashrc; \
    echo "alias a=alias" >> /home/TODO-UID/.bashrc; \
    echo "alias ver='cat /etc/lsb-release'" >> /home/TODO-UID/.bashrc; \
    echo "export PATH=$PATH:/usr/games" >> /home/TODO-UID/.bashrc; \
    echo "cd" >> /home/TODO-UID/.bashrc; \
    echo "fortune|cowsay" >> /home/TODO-UID/.bashrc; \
    echo "date" >> /home/TODO-UID/.bashrc; \
    chown -R TODO-UID:dockeruser /home/TODO-UID/.bashrc

# create new .bash_profile
RUN echo "if [ -f ~/.bashrc ];" > /home/TODO-UID/.bash_profile; \
    echo "then" >> /home/TODO-UID/.bash_profile; \
    echo "  source ~/.bashrc" >> /home/TODO-UID/.bash_profile; \
    echo "fi" >> /home/TODO-UID/.bash_profile; \
    chown -R TODO-UID:dockeruser /home/TODO-UID/.bash_profile

# create new .vimrc
RUN echo ":syntax off" > /home/TODO-UID/.vimrc; \
    chown -R TODO-UID:dockeruser /home/TODO-UID/.vimrc

USER TODO-UID