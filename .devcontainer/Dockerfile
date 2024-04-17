FROM debian:bookworm-slim

RUN apt-get update && \
  apt-get install -y \
    build-essential \
    inkscape \
    gnupg2 \
    software-properties-common \
    python3-pip \
    python3-venv \
    git-core \
    zsh \
    fonts-powerline \
    locales \
    wget \
    zip \
    curl \
    vim
RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && /usr/sbin/locale-gen
ENV TERM xterm
ENV SHELL /bin/zsh
RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
RUN git clone https://github.com/romkatv/powerlevel10k.git ~/.oh-my-zsh/custom/themes/powerlevel10k
RUN ls -al $HOME && mkdir -p $HOME/.local/ConTeXt && cd $HOME/.local/ConTeXt && \
    wget https://lmtx.pragma-ade.com/install-lmtx/context-linux-aarch64.zip && \
    unzip context-linux-aarch64.zip && \
    rm context-linux-aarch64.zip && \
    sh install.sh && \
    export PATH=$HOME/.local/ConTeXt/tex/texmf-linux-aarch64/bin:$PATH && \
    mtxrun --generate

COPY .zshrc /root/
COPY .p10k.zsh /root/
COPY xdg-open /usr/local/bin/xdg-open
