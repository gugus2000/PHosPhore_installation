# PHosPhore_installation

***DO NOT USE IT UNTIL IT IS FIXED (this message will be removed)***

An installation module for the PHosPhore PHP framework

## Getting started

This installation module allow to automatically set framework's option

## Prerequisites

- PHosPhore framework

## Installation

Drag and drop the files into the [src](src) folder into your PHosPhore root directory (which contains ``index.php``).

## How to use

This module is needed before the first loading of PHosPhore.
After its installation, load the page like any hosted website. Then, if all works, you can delete it.

## How its work

This module add a single hook named ``phosphore_installation.php`` after the logger initialisation (at [core/index/start_after_logger](src/hook/core/index/start_after_logger)).
- The hook load the config, lang and locale file of the module, and checks if the [installed_file]() exists, which mean the mod is already installed.
- If the [installed_file]() does not exist, the script start the installation, if it does, the framework load directly.
- It checks if the [secret_file]() exists, and if not, generates it.
- It checks if secret was given before, and store it in session if it is.
- It checks if the secret stored in session exist and is valid, if it's invalid, the hook generate a new secret, if it does not exist, the script generate a form to enter it.
- It checks in which stage the script is, using the [stage_file]() or trying the database connection if it does not exist.

### Stage 0

The hook generate a form to enter the parameter to generate a configuration file and a database

### Stage 1

The hook:
- generate a config file with the given parameter
- generate the database with the given parameter
- delete the [stage_file](), the [secret_file]() and create the [installed_file]()
- continue the loading of the framework

## Authors

- **gugus2000** - *intial work*

## Versioning

We use [SemVer](http://semver.org/) for versioning.

## License

This project is licensied under the Chocolate-Ware License - see the [LICENSE](LICENSE) file for more information
