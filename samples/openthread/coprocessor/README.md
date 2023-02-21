#

## Build

```bash
docker compose run --rm nrf west build -b nrf52840dongle_nrf52840 -- -DOVERLAY_CONFIG="overlay-usb.conf" -DDTC_OVERLAY_FILE="usb.overlay"
```

## Flash

```bash
docker compose run --rm nrf nrfutil pkg generate \
        --hw-version 52 --sd-req=0x00 \
        --application build/zephyr/zephyr.hex \
        --application-version 1 first.zip

docker compose -f docker-compose.yml -f docker-compose.device.yml run nrf \
        nrfutil dfu usb-serial -pkg first.zip -p /dev/ttyACM2
```
