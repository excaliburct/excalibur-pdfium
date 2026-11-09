# PDFium for iOS 15

The PDF engine inside Excalibur View's iPad and iPhone app, built so the app runs on iOS 15 and later.

The ready-made engine View used (bblanchon/pdfium-binaries, chromium/8066) is built for iOS 17 and later, which kept
older iPads out. This repository builds the same engine with the same scripts, at the same commit, and changes one
setting: the iOS minimum, 15.0 (Apple's floor for App Store apps built with Xcode 26).

- `.github/workflows/ios.yml` runs on GitHub's Macs. A hand run builds and keeps the two packages (device and
  simulator). A tag such as `chromium/8066-ios15` builds them and makes a release with `SHA256SUMS.txt`.
- Each build checks that the library really says `minos 15.0` before it is kept.
- View's `mobile/ios/build.sh` downloads the packages from that release and checks each against the SHA-256 pinned in
  View, so a package can never change underneath it.

PDFium and the build scripts keep their own licences (BSD-3-Clause and MIT); each package carries them in
`licenses/`.
