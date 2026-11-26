# cub-plugins

The index of known plugins for `cub`, the ConfigHub CLI.

A known plugin is one `cub` can install by name, and by the commands it provides: typing a command that a known plugin provides installs the plugin and runs the command. This needs cub v0.11.18 or newer.

```sh
cub plugin list --all        # installed plugins, and known ones that are not
cub installer --help         # installs the installer plugin, then runs it
cub plugin install helm      # or install one by name
```

`cub` reads this repository at most once a day, so a change here reaches every `cub` within a day. Set `CUB_PLUGIN_AUTO_INSTALL` to `never` to be told the install command instead, `ask` to be asked first, or `auto` to never be asked.

## Entries

Each plugin has one file, `plugins/<name>.yaml`:

```yaml
name: installer
source: confighub/installer
commands: [installer]
prompt: false
```

| Field | Meaning |
|---|---|
| `name` | The name the plugin is installed under, and the name `cub plugin install <name>` accepts. Matches the file name. |
| `source` | The GitHub `owner/repo` that publishes the plugin's releases. |
| `commands` | The top-level `cub` commands, and their aliases, that the plugin provides. |
| `minCubVersion` | Optional. The oldest `cub` the plugin works with. |
| `prompt` | Optional. Whether `cub` asks before installing. The default is `true`. |

An entry holds nothing specific to a plugin version. `cub` installs the latest release from `source`, so releasing a plugin needs no change here. Change an entry when a plugin is added or the commands it provides change.

A command belongs to one plugin, and no plugin claims a command that `cub` has built in.

## Scope

The index holds ConfigHub's own plugins for now.

## License

MIT. See [LICENSE](LICENSE).
