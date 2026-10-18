# LumaLink — beta testing and feedback

LumaLink is an early prototype that helps configure selected Home Assistant lights and switches for **Amazon Alexa**, **Siri / Apple Home**, or **Google Home**.

The underlying Home Assistant integrations are already available for free. The proposed product adds configuration previews, compatibility checks, private backups, native configuration validation, and protected rollback. A one-time price of **€20 is being considered**; the prototype is not currently for sale.

## Looking for volunteer hardware testers

We are particularly looking for people who already have an iPhone / Apple Home setup or a Google Home / Nest device and a separate Home Assistant test installation. **No purchase is requested.**

Please join the [tester recruitment issue](https://github.com/NoisyBoyFR/lumalink-beta/issues/1) and describe your available setup. This repository currently contains feedback and testing information only. The prototype source and installer have **not** been published here; access to a test package will be arranged after the beta packaging and distribution terms have been settled.

## Current validation

- 76 automated tests pass on Linux, including backup and rollback protections, YAML conflicts, permissions, symlinks, and prevention of token forwarding on HTTP redirects.
- An independent installation has successfully executed an Alexa voice command through Home Assistant's native Emulated Hue bridge. The exact Echo model used for that command was not recorded.
- HomeKit and Google configuration schemas have been checked against Home Assistant 2026.10.2. These checks are **not** end-to-end Siri or Google Home voice tests.
- Hardware discovery, pairing, account linking, and voice commands still need independent testing for each supported setup.

## First-version scope

The installer currently targets **Home Assistant Container on Linux**, with Docker host networking and a writable bind-mounted `/config` directory. It exposes only explicitly selected `light.*` and `switch.*` entities, with a conservative limit of 49.

| Assistant | Connection | What still requires user action |
|---|---|---|
| Alexa | Native Emulated Hue bridge on the local LAN | Discover the Philips Hue V1 bridge and verify a voice command on a compatible Echo |
| Siri / Apple Home | Native HomeKit Bridge | Pair the bridge in Apple Home using Home Assistant's QR/code and verify Siri |
| Google Home | Native Google Assistant integration | Provide a personal Cloud-to-cloud project, service-account file and public HTTPS Home Assistant endpoint; finish account linking and verify a command |

This is not a universal replacement for Home Assistant Cloud. Google Home does not use the Alexa Hue path. Alexa still uses Amazon's service for voice recognition. LumaLink does not open router ports, create cloud accounts, publish Home Assistant, or rename devices already cached in Alexa.

## Testing expectations

Use a disposable or properly backed-up test setup. Begin with one non-critical light, review the generated plan, and test rollback before adding more devices. Do not include locks, alarms, doors, heating, or other safety-sensitive equipment in the lighting selection.

Reports should include the assistant/device model and firmware, Home Assistant version, installation type, operating system/CPU architecture, selected connection method, exact test steps, expected result, and actual result. State separately whether configuration validation, pairing, and a real voice command succeeded.

**Never post tokens, passwords, private keys, full configuration files, household addresses, or unredacted logs.** There is no need to share account access with a tester or maintainer.

No affiliation with or certification by Home Assistant, Amazon, Google, Apple, or Philips Hue is claimed.

### Documentation for the native integrations

- [Home Assistant Emulated Hue](https://www.home-assistant.io/integrations/emulated_hue/)
- [Home Assistant HomeKit Bridge](https://www.home-assistant.io/integrations/homekit/)
- [Home Assistant Google Assistant](https://www.home-assistant.io/integrations/google_assistant/)

### En français

Nous recherchons des volontaires disposant déjà d'un iPhone/Apple Maison ou d'un Google Home/Nest pour tester ce prototype sur une installation de test. Le programme n'est pas encore commercialisé. Le code n'est pas publié dans ce dépôt de retours ; les modalités d'accès à la bêta seront précisées avant les essais.
