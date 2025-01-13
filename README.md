# Cloudflared ARMv8 Build Repository

Unofficial builds for Raspberry Pi 1, Zero, and Zero W

[![Build Cloudflared](https://github.com/IndraGunawan/cloudflared-armv6/actions/workflows/build.yaml/badge.svg)](https://github.com/IndraGunawan/cloudflared-armv6/actions/workflows/build.yaml)

## Build Repository Only

This repo **ONLY PROVIDES BINARIES FOR ARMv6 DEVICES AND DOES NOT ALTER SOURCE CODE** for the Cloudflared repo. For software issues regarding Cloudflared, go to the [Cloudflared repo](https://github.com/cloudflare/cloudflared) and open an issue there.

armv8路径启动脚本
```
#!/bin/bash

cloudflareHome=/tmp/cloudflare
# 创建目标目录
mkdir -p $cloudflareHomee

token=你的TOKEN
# 定义文件路径和下载URL
FILE_PATH=${cloudflareHome}/cloudflared
DOWNLOAD_URL="https://github.com/momocstar/cloudflared-armv8/releases/download/2025.1.0-5/cloudflared"

# 判断文件是否存在
if [ ! -f "$FILE_PATH" ]; then
  echo "File not found. Downloading..."
  wget -O "$FILE_PATH" "$DOWNLOAD_URL"
  chmod a+x "$FILE_PATH"
else
  echo "File already exists. Skipping download."
fi

# 启动cloudflared
nohup "$FILE_PATH" --no-autoupdate tunnel run --token $token > $cloudflareHome/nohup.out 2>&1 &

echo "Cloudflared started."
```
