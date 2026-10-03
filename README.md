# Centra Tab Community

Clipboard history across Windows, macOS and Linux computers on **your own Tailscale network**.

Download the installer for your computer from [Releases](https://github.com/KnickQueue/Centra-Tab-Releases/releases/latest). Windows uses the x64 Setup.exe; Apple Silicon Macs use the arm64 DMG; Linux x64 uses the AppImage (or the Debian package).

## Connect your computers

1. Install Centra Tab Community and sign each computer into your own Tailscale network.
2. The first-run assistant keeps capture paused until you finish setup. Choose a central server, an existing server, automatic computer hosting, or local history.
3. For a new NAS/server, save the server kit from the assistant. Copy its entire folder to a server running Docker Compose and Tailscale, then follow its README. The kit contains everything needed to run the encrypted history server, with Docker and TrueNAS instructions.
4. Paste the server's Tailscale HTTPS address and access token into the assistant and test it. Your first computer generates the workspace encryption key; the server never receives that key.
5. Save a password-protected connection file and import it on your other computers. Alternatively, use automatic discovery inside your tailnet. Any connected computer can approve newcomers; approval is enabled by default in the Community edition and controlled per computer.
6. Select a shared history item to put it on your local clipboard, then paste into your application normally.

Clipboard text and images are encrypted before being saved or shared. Credentials use the operating system's credential store when available. Keep a recovery connection file and its password separately.

## Remote desktop and repeated copies

Use **All machines** to select several computers together. Enable **Hide duplicates** to show repeated text or images once within that view. The app shows the latest matching capture, its copy count and source machines. It compares text with consistent line endings and images by their decoded pixels. All captures stay stored; pin/delete affect the displayed capture. Your view preferences are remembered.

Scroll with your mouse wheel or touchpad. Refreshes and incoming captures keep your reading position; arrow keys keep the selected entry in view.

## History cache and replayed copies

Open **History cache** to choose 1–3650 days for this computer (default 7). Disable **Keep pinned items** if pinned copies should expire too. Shortening the period removes older local copies immediately; it does not delete history on other computers. The central server has its own retention policy, set through RETENTION_DAYS in its Docker Compose file.

**Copy to clipboard** reuses a saved item without capturing it again. Replay markers, content normalization, and authenticated notices to connected app instances suppress immediate remote-desktop echoes. Update both ends to 0.6.0 or later for this protection when the remote software strips clipboard markers. Peers that miss the notice or very delayed echoes may still create a copy; Hide duplicates remains available.

## App updates

The app checks this public GitHub release feed automatically and downloads signed updates without a GitHub account. Choose **Updates → Restart & update** to install. Windows updates through its installer; macOS updates the installed app in a writable Applications folder; Linux supports in-app updates for writable AppImages. Debian installs use the package manager. Release metadata is Ed25519 signed and installers are checked against their signed SHA-512 hashes. Your workspace token and key are never sent to GitHub.

## Android preview

Download the signed APK from the [Android preview release](https://github.com/KnickQueue/Centra-Tab-Releases/releases/tag/android-v0.1.1). Android 11+ is supported. Connect Tailscale on your phone, then enter your own tailnet name and a connected computer's full Tailscale hostname in the guided setup. The computer supplies your existing server connection through encrypted pairing; approve the phone on that computer if approval is enabled. Manual central-server setup and protected connection files are also available.

The phone uses Android Keystore for saved credentials and shares encrypted text and PNG history with desktop members. Use Capture clipboard while the app is open, enable optional capture while focused, or Share text/images to Centra Tab from other apps. Optional background sync runs with a notification and Stop control. Android restricts background clipboard reads; background capture needs the compatible NuBoard keyboard bridge, enabled in both NuBoard Clipboard Manager Settings and Centra Tab Settings while NuBoard is the default keyboard. Only copied text/images are forwarded locally for encryption; sensitive items, Centra Tab replays and typing are excluded. Each user keeps their own Tailscale network and hub. Touch scrolling, several-machine checkboxes, duplicate grouping, cache retention, pins, and copy suppression are included. Settings can check signed APK updates; Android confirms the installation. Android preview releases use a separate update channel and do not replace the desktop stable release.

## Preview limitations

This is a working preview: Windows installers do not yet have an Authenticode certificate, and macOS builds are ad-hoc signed, without Apple notarization. Apple Silicon, Windows x64 and Linux x64 are the initial targets. Linux clipboard access depends on the desktop/compositor. If your Linux system lacks libfuse2, run the AppImage with APPIMAGE_EXTRACT_AND_RUN=1, or use the Debian package on a compatible distribution.

This repository holds installers, signed update metadata and this guide. Development source remains in a separate private repository. Each household/team runs its own Tailscale network and server; this project does not provide a shared hosted clipboard service.
