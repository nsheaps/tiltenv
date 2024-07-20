# tiltenv
Make managing multi-service tilt deployments easier

Note, if `tiltenv` is run from this folder, it defaults to using the `config.yaml` in the root of this directory, by slipping `./bin/` into the front of the path using direnv. The `tiltenv` script in that folder overrides the config by passing `--config-dir` to be the root of the git folder.

| Command         | Description     |
|---|---|
| tiltenv workspace create |                  Creates a new workspace and workspace state (if it doesn't already exist) |
| tiltenv workspace destroy |                 Destroys associated workspace objects, including state |
| tiltenv workspace status |                  Prints current workspace state |
| tiltenv workspace doctor |                  Diagnoses current issues with workspace|
| tiltenv service enable service-name ... |   Checks for the service code to be downloaded (skips if no gitOrigin), then enables the workspace in the state. While tilt is running, it monitors for workspace state changes and will trigger a reload to launch any newly enabled services |
| tiltenv service disable service-name ... |  |
| tiltenv service search query |              |
| tiltenv service info service-name |         |
| tiltenv up |                                |
| tiltenv ci |                                |
| tiltenv config-dir |                        |
| tiltenv autocompletr zsh\|bash |            |
| tiltenv install <configOrigin> |            Symlinks tiltenv (via `$HOME/.local/bin`, and make sure that's in `.zshrc`'s or `.bashrc`'s path set up) to automatically run from a particular configuration<br>If a config origin is provided, the config.yaml will be read from the root fo that repo and executed from there.<br>If no config origin is provided, it will link the current tiltenv binary, which if you're in the repo is `./bin/tiltenv` |
| tiltenv version |                           |
| tiltenv upgrade |                           Looks for the source of the `tiltenv` binary and upgrades it if possible. If a git repo, it will git pull, if brew, it will attempt to upgrade it from the upstream tap. |
| tiltenv update |                            Updates config and services. Does not update tiltenv itself |
| tiltenv update-config |                     cd to `tiltenv.configRoot` and `git pull`. Does not switch branches. tiltenv sets tilt to watch the config file, so this will trigger a reload |
| tiltenv update-services |                   iterate through every enabled service's directory and git pull. tiltenv sets tilt to watch the git files, so this will trigger a reload |

## First time setup
1. Set up `direnv`, make sure to set up the shell hooks in your rc file
2. Clone this repository and `cd` into it
3. Run `brew bundle` to install dependencies
4. Run `tiltenv install` to install the tiltenv binary
