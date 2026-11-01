# Set up CARBON

## Build and launch

Install JDK 17 and Android SDK Platform 35. Set `ANDROID_HOME` or create an untracked `local.properties` pointing to your SDK. Run `./gradlew :app:assembleDebug`, install the debug APK on your own Android TV with ADB, and launch CARBON once.

Use your TV's supported default-home selector if it offers one. Vendor firmware may ignore alternate launchers or briefly show Google TV. Keep access to the original launcher and TV settings. No rooting procedure is supplied.

## Provider keys

Run `python3 tools/setup.py --device YOUR_ADB_SERIAL --provider PROVIDER`. Supported provider names are `fireworks`, `sarvam`, `tmdb`, and `agentmail`. Input is hidden. The tool reads the app's exported public key, encrypts the credential, and transfers the encrypted file. Verify the import result on the TV. Disable ADB after setup when it is no longer needed.

Use credentials you own. Configure only integrations you plan to use. Never paste a key into an issue, screenshot or commit.

## Personal configuration

Copy `config.example.json` to `carbon-config.json`. This filename is ignored by Git. Set your local model, endpoint, provider model, recipient, inbox and permitted stream URLs as needed. Empty values are not account credentials. Import with:

```sh
python3 tools/setup.py --device YOUR_ADB_SERIAL --config carbon-config.json
```

This restarts CARBON to import configuration. Keep your private configuration out of shared archives.

## Ollama on a local computer

Install and run Ollama on your computer and download a compatible model. For development, `adb reverse tcp:11434 tcp:11434` maps the app's localhost endpoint to the computer. Use the configured model name and choose private local mode in CARBON. A separate TV-to-computer endpoint requires HTTPS in the public build. Do not expose an unauthenticated model server to the public internet.

Local-only mode does not silently send AI requests to the cloud. Cloud speech is a separate option, and online streaming apps remain online.

## Email and live TV

Configure your own AgentMail inbox and recipient, then test with non-sensitive content. Sending requires an explicit user action.

Live TV entries require user-provided stream configuration. Only configure streams you have permission to access. This project supplies no subscription credentials or promise of permanent free channel availability.

## Casting and microphone compatibility

AirPlay and Android Cast use receivers already supported by your TV. They are not newly implemented casting protocols. Remote dictation depends on Android's speech service and the device's microphone route. Continuous hands-free conversation is experimental and hardware-dependent.
