# Zen Browser

This is a flake for the Zen browser.

Just add it to your NixOS `flake.nix` or home-manager:

```nix
inputs = {
  zen-browser.url = "github:0xpetersatoshi/zen-browser-flake";
  ...
}
```

Then in either `home.packages` (if using home-manager) or `environment.systemPackages` in your nix configuration
add:

```nix
inputs.zen-browser.packages."${system}".default
```

## 1Password

Zen has to be manually added to the list of browsers that 1Password will communicate with. See
[this wiki article](https://nixos.wiki/wiki/1Password) for more information. To enable 1Password integration, you need
to add the line `.zen-wrapped` to the file `/etc/1password/custom_allowed_browsers`.

## Updating Zen Version

To update the zen browser version, update the `version` variable in the [flake.nix](./flake.nix) file as well as the
`sha256` value.

To get the new sha256 value, run this command with the updated version number:

```bash
version=1.7.6b; nix-prefetch-url "https://github.com/zen-browser/desktop/releases/download/${version}/zen.linux-x86_64.tar.xz" --type sha256 --unpack
```
