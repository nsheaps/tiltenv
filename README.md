# tiltenv
Make managing multi-service tilt deployments easier

Note, if `tiltenv` is run from this folder, it defaults to using the `config.yaml` in the root of this directory, by slipping `./bin/` into the front of the path using direnv. The `tiltenv` script in that folder overrides the config by passing `--config-dir` to be the root of the git folder.

| Command         | Description     |
|---|---|
| tiltenv workspace create |                  Creates a new workspace and workspace state (if it doesn't already exist) |
| tiltenv workspace destroy |                 Destroys associated workspace objects, including state |
| tiltenv workspace status |                  Prints current workspace state |
| tiltenv workspace get-context |             If using a k8s workspace provider, will print expected context. If current context provider, will exit -1 but still print global context to stdout. Else exit's 1 |
| tiltenv workspace doctor |                  Diagnoses current issues with workspace|
| tiltenv service enable service-name ... |   Checks for the service code to be downloaded (skips if no gitOrigin), then enables the workspace in the state. While tilt is running, it monitors for workspace state changes and will trigger a reload to launch any newly enabled services |
| tiltenv service disable service-name ... |  |
| tiltenv service search query |              |
| tiltenv service info service-name |         |
| tiltenv up |                                |
| tiltenv ci |                                |
| tiltenv config-dir |                        |
| tiltenv autocompletr zsh\|bash |            |
| tiltenv set-config <configOrigin> |          Sets up `$HOME/.tiltenv/config.yaml` to automatically run from a particular configuration<br>If a config origin is provided, the config.yaml will be read from the root fo that repo and executed from there.<br>Otherwise, it will link to the config dir provided (defaults to gitroot of current dir if not provided) |
| tiltenv develop |                           Symlinks tiltenv (if not root then via `$HOME/.local/bin`, and make sure that's in `.zshrc`'s or `.bashrc`'s path set up. If root, in `/usr/local/bin`). Note: if tiltenv is running from the same folder as the configDir, it will get updated when the config is updated. |
| tiltenv version |                           |
| tiltenv upgrade |                           Looks for the source of the `tiltenv` binary and upgrades it if possible. If a git repo, it will git pull, if brew, it will attempt to upgrade it from the upstream tap. |
| tiltenv update |                            Updates config and services. Does not update tiltenv itself |
| tiltenv update-config |                     cd to `tiltenv.configRoot` and `git pull`. Does not switch branches. tiltenv sets tilt to watch the config file, so this will trigger a reload |
| tiltenv update-services |                   iterate through every enabled service's directory and git pull. tiltenv sets tilt to watch the git files, so this will trigger a reload |

## First time setup

> [!TIP] Just looking to install tiltenv?
> Install with `brew install nsheaps/devsetup/tiltenv`

1. Set up `direnv`, make sure to set up the shell hooks in your rc file
2. Clone this repository and `cd` into it
3. `direnv allow .` which will make sure all dependencies are installed
   - Python 3.11 or higher
   - [Poetry](https://python-poetry.org/)
4. Run `brew bundle` to install dependencies
5. [Optional] Run `tiltenv develop` to install the tiltenv binary from this repo into a system path.
   If you do, `tiltenv` will always run from the git repo instead of the one installed by brew.
