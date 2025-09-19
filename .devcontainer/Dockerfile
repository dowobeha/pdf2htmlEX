FROM swift:bookworm

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID


# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo vim less file \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# [Optional] Set the default user. Omit if you want to keep the default as root.
USER $USERNAME

# Core packages needed only at build-time + runtime libs
#RUN apt update && apt install -y \
#    git curl wget make g++ pkg-config cmake \
#    autoconf automake libtool dpkg-dev           \
#    fontforge poppler-utils                      \
#    libpng-dev zlib1g-dev libfreetype6-dev       \
#    libjpeg-dev libopenjp2-7-dev                 \
#    libxml2-dev gettext jq

#WORKDIR /app

# ---------- build pdf2htmlEX ----------
#RUN git clone https://github.com/pdf2htmlEX/pdf2htmlEX.git && \
#    cd pdf2htmlEX && \
#    \
#    # 1) nuke all 'sudo ' strings (the scripts assume sudo)
#    sed -i 's/sudo //g' buildScripts/* && \
#    \
#    # 2) drop the obsolete Java-8 dependency ­(not in Bookworm ARM64)
#    sed -i '/openjdk-8-jre-headless/d' buildScripts/getBuildToolsApt && \
#    \
#    # 3) run their meta-build script as root
#    ./buildScripts/buildInstallLocallyApt && \
#    \
#    # ---------- optional clean-up ----------
#    # remove big build tool-chains to slim the final image
#    apt purge -y \
#        git curl wget make g++ pkg-config cmake \
#        autoconf automake libtool dpkg-dev build-essential && \
#    apt autoremove -y && \
#    apt clean && \
#    rm -rf /var/lib/apt/lists/* /root/.cache

# ---------- default command ----------
ENTRYPOINT ["pdf2htmlEX"]

