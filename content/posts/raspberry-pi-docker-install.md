+++
title="Install Docker on Raspberry Pi one-liner"
date=2022-05-24
extra.tldr=""
+++

```bash
sudo apt-get update && sudo apt-get upgrade -y && curl -fsSL https://get.docker.com | sudo sh && sudo usermod -aG docker $USER
```