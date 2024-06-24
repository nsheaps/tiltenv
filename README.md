# tiltenv
Make managing multi-service tilt deployments easier

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
| tiltenv install |                           When installed, the tiltenv binary is added to the path and  |
| tiltenv version |                           |
| tiltenv update |                            |

## First time setup
1. Clone this repository
2. Run `brew bundle` to install dependencies
3. Run `tiltenv install` to install the tiltenv binary
