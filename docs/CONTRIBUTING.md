# Contributing

The core of this project is a set of JSON files which describe what telemetry is collected and what can be done to enable or disable it. Tests and README generator are using PowerShell Core.

## Prerequisites

While you can hack around without using provided build script, it is not recommended. To run the build and tests, you'll need [PowerShell Core](https://github.com/powershell/powershell).

On non-Windows systems [Mono](https://www.mono-project.com/) is required for build script to be able to run [Paket](https://fsprojects.github.io/Paket/) to restore dependecies.

## Adding new telemetry data file

See [data/README](/data/README.md)

## Using build script

Contributions need to pass the tests and provide a generated `README.md` file. Build script takes care of that.

### Tasks

The provided `build.ps1` script includes several tasks:

- `test`: run code and data files tests
- `readme`: generate `README.md`
- `shell`: generate [example shell scripts](/example)
- `clean-all`: clean global and local NuGet and cache directories
- `clean`: clean local NuGet and cache directories

If the build script is run without arguments the `test` and `readme` tasks are executed. To execute specific task provide its name as an argument: `.\build.ps1 readme`. For more details see [Invoke-Build](https://github.com/nightroman/Invoke-Build) docs.

### Dependencies

Script and tasks require several dependencies from the [PowerShell Gallery](https://www.powershellgallery.com/). To avoid polluting your environment those dependecies are downloaded on the first run into the `./packages` directory. This is achieved by using [Paket](https://fsprojects.github.io/Paket/) in [magic mode](https://fsprojects.github.io/Paket/bootstrapper.html#Magic-mode).
