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

## Updates

The app checks this public GitHub release feed automatically and downloads signed updates without a GitHub account. Choose **Updates → Restart & update** to install. Windows updates through its installer; macOS updates the installed app in a writable Applications folder; Linux supports in-app updates for writable AppImages. Debian installs use the package manager. Release metadata is Ed25519 signed and installers are checked against their signed SHA-512 hashes. Your workspace token and key are never sent to GitHub.

## Preview limitations

This is a working preview: Windows installers do not yet have an Authenticode certificate, and macOS builds are ad-hoc signed, without Apple notarization. Apple Silicon, Windows x64 and Linux x64 are the initial targets. Linux clipboard access depends on the desktop/compositor. If your Linux system lacks libfuse2, run the AppImage with APPIMAGE_EXTRACT_AND_RUN=1, or use the Debian package on a compatible distribution.

This repository holds installers, signed update metadata and this guide. Development source remains in a separate private repository. Each household/team runs its own Tailscale network and server; this project does not provide a shared hosted clipboard service.
