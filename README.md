# TS0044 six-endpoint ZHA quirk

This repository contains a ZHA custom quirk for a Tuya TS0044-style four-key remote whose device signature reports six endpoints.

## What the quirk matches

The quirk signature matches:

- Model: `TS0044`
- Six reported endpoints: `1` through `6`
- The endpoint profile, device type, and cluster layout declared in `ts0044_6endpoint_quirk.py`

The signature does **not** restrict the manufacturer or firmware version. Because of that, a different device with a compatible-looking signature may be matched accidentally. Use this quirk only after checking the device signature and be aware of the risk of a false match.

## Declared triggers

The code declares ZHA device automation triggers for the four physical buttons on endpoints 1–4:

- Short press
- Long press
- Double press

These behaviors are declarations in the code. They have **not been verified on real hardware in the current session**.

## Installation in Home Assistant ZHA

1. Copy `ts0044_6endpoint_quirk.py` to a directory on the Home Assistant host, for example:

   ```text
   /config/zha_quirks/ts0044_6endpoint_quirk.py
   ```

2. In Home Assistant, open **Settings → Devices & services → ZHA → Configure** and set **Custom quirks path** to the directory containing the file, for example:

   ```text
   /config/zha_quirks
   ```

   If you already have a ZHA custom quirks path configured, merge this file into that existing directory and keep the existing path configuration. Do not replace or remove existing custom quirks.

3. Restart Home Assistant so ZHA reloads the custom quirk.

4. Open the device in ZHA and verify that the quirk is selected and that the device exposes the expected remote behavior and triggers. Check the device signature before relying on it in automations.

A restart and verification are normally sufficient. There is no need to immediately re-pair the remote. Re-pairing may be considered only if the existing device does not reload or recognize the quirk after the restart, and should follow your normal ZHA recovery procedure.

## Limitations

- No manufacturer or firmware restriction is included in the signature.
- A signature match does not guarantee that every device behaves identically.
- The four-button short-press, long-press, and double-press triggers are not real-device-validated here.
- This repository does not include logs, private information, or pairing data.

## License

No license was provided with this file. This repository does not add or imply a license, ownership attribution, or warranty.
