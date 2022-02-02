# Build rednodelabs/otbr:base docker

docker buildx build --platform linux/arm/v7 --build-arg WEB_GUI=0 --build-arg REST_API=0 --build-arg BACKBONE_ROUTER=0 --build-arg OTBR_OPTIONS='-DOT_THREAD_VERSION=1.1' -t rednodelabs/otbr:base -f etc/docker/Dockerfile --push .

## Local build
WEB_GUI=0 REST_API=0 OTBR_OPTIONS='-DOT_THREAD_VERSION=1.1' ./script/localbuild

./build/otbr/src/agent/otbr-agent -I wpan0 -v 'spinel+hdlc+uart:///dev/ttyACM0?uart-baudrate=1000000' -d 6
