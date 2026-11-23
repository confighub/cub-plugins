# cub-plugins

The index of known plugins for `cub`, the ConfigHub CLI.

A known plugin is one `cub` can install by name, and by the commands it provides: typing a command that a known plugin provides installs the plugin and runs the command. Support for this in `cub` is in progress; until it is released, install a plugin with `cub plugin install <source>`.

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
