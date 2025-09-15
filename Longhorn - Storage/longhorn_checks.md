https://longhorn.io/docs/1.9.1/deploy/install/
# For AMD64 platform
curl -sSfL -o longhornctl https://github.com/longhorn/cli/releases/download/v1.9.1/longhornctl-linux-amd64
# For ARM platform
curl -sSfL -o longhornctl https://github.com/longhorn/cli/releases/download/v1.9.1/longhornctl-linux-arm64

chmod +x longhornctl
./longhornctl check preflight

install options
./longhornctl install preflight

# Disabling multipath (not required on most systems)
systemctl stop multipathd
systemctl disable multipathd