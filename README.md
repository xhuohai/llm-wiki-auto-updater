# LLM Wiki Auto-Updater

This repository automates the maintenance and updating of the Arch Linux User Repository (AUR) package `llm-wiki-bin`, which provides the LLM Wiki desktop application.

## What is LLM Wiki?

LLM Wiki is a cross-platform desktop application that transforms your documents into an organized, interlinked knowledge base — automatically. It helps users build and manage their personal wiki from various document sources.

For more information, visit the [official GitHub repository](https://github.com/nashsu/llm_wiki).

## Purpose

This project uses GitHub Actions to:
- Monitor the upstream GitHub repository for new releases
- Automatically update the AUR package when new versions are available
- Verify package builds and publish updates to AUR
- Maintain version tracking and commit changes back to this repository

## How It Works

1. **Scheduled Checks**: Runs every 4 hours via GitHub Actions cron schedule
2. **Version Detection**: Uses `nvchecker` to detect new releases on GitHub
3. **Build Verification**: Downloads and verifies the package builds correctly in an Arch Linux container
4. **AUR Publishing**: Updates the AUR repository with new versions using SSH
5. **State Tracking**: Commits version changes back to this repository

## Files

- `PKGBUILD`: Arch Linux package build script
- `nvchecker.toml`: Configuration for version checking
- `nvchecker_oldver.json`: Tracks current package versions
- `.github/workflows/update_and_pack_paseo.yml`: GitHub Actions workflow for automation

## Manual Usage

To manually check for updates or trigger the workflow:

1. Run `nvchecker -c nvchecker.toml` to check for new versions
2. If updates are found, update `PKGBUILD` with the new version
3. Run `updpkgsums` to update checksums
4. Test build with `makepkg -si`
5. Commit and push changes

## Contributing

Contributions are welcome! Please open issues or pull requests for improvements.

## License

This repository is licensed under GPL-3.0-only, matching the upstream project.