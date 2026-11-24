# Home Assistant Change Notes

## 1. Boiler relay runtime limit

**Updated.** The backup shutoff in [automations.yaml](automations.yaml) now reads `last_changed` from the relay's state object and checks every five minutes for a runtime of at least three hours. In [scripts.yaml](scripts.yaml), the heating script now waits up to three hours for the temperature helper before proceeding to relay shutoff. A timeout skips the success timestamp and email. The script continues if the start email fails.

## 2. Automation include filename

**Resolved.** The file was renamed from `automation.yaml` to `automations.yaml`, matching the include in [configuration.yaml](configuration.yaml).

## 3. Overnight boiler helper

**Resolved in the current YAML.** The overnight relay condition and the due-date automation now both use `input_boolean.twe_legionellenschutz_fallig_nacht`. The earlier mismatch could prevent a due overnight heating cycle from starting.

## 4. Duplicate dehumidifier definitions

**Updated.** Removed the second definition for each of the four Werken and Technik day and night automations. A before-and-after comparison confirmed that all retained definitions were identical and stayed in the same order. The automation file has 11 unique IDs.

## 5. Dehumidifier handoff at 21:00

**Open.** The night rules can start on Home Assistant startup, a night runtime limit change, or demand switching on. If demand is already on at 21:00, the clock alone does not start night operation. Day and night also share each room's `laufzeit_heute` counter, so daytime runtime counts toward the night limit. Confirm whether the night setting should be a total daily cap or a separate allowance before changing it.

## Further Changes

