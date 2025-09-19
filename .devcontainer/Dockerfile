FROM swift:bookworm

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
ARG DEBIAN_FRONTEND=noninteractive

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo vim less file \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# [Optional] Set the default user. Omit if you want to keep the default as root.
USER $USERNAME

RUN apt-get update

RUN apt-get -y install --no-install-recommends git
RUN apt-get -y install --no-install-recommends curl
RUN apt-get -y install --no-install-recommends wget
RUN apt-get -y install --no-install-recommends make
RUN apt-get -y install --no-install-recommends g++
RUN apt-get -y install --no-install-recommends pkg-config
RUN apt-get -y install --no-install-recommends cmake
RUN apt-get -y install --no-install-recommends autoconf
RUN apt-get -y install --no-install-recommends automake
RUN apt-get -y install --no-install-recommends libtool
RUN apt-get -y install --no-install-recommends dpkg-dev
RUN apt-get -y install --no-install-recommends fontforge
RUN apt-get -y install --no-install-recommends poppler-utils
RUN apt-get -y install --no-install-recommends libpng-dev
RUN apt-get -y install --no-install-recommends zlib1g-dev
RUN apt-get -y install --no-install-recommends libfreetype6-dev
RUN apt-get -y install --no-install-recommends libjpeg-dev
RUN apt-get -y install --no-install-recommends libopenjp2-7-dev
RUN apt-get -y install --no-install-recommends libxml2-dev
RUN apt-get -y install --no-install-recommends gettext
RUN apt-get -y install --no-install-recommends jq
