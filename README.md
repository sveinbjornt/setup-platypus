# Platypus GitHub Action

This action installs [Platypus](https://sveinbjorn.org/platypus), a developer tool that creates native macOS applications from command line scripts (Shell, Python, Perl, Ruby, PHP, JavaScript, etc.).

It can be used to simply setup Platypus in your workflow, or to directly build an application bundle from a script.

## Usage

### Basic Usage (Build an App)

```yaml
steps:
  - uses: actions/checkout@v4
  
  - name: Build macOS App
    uses: sveinbjornt/action-platypus@v1
    with:
      script: 'myscript.sh'
      name: 'My App'
      output: 'My App.app'
      interface: 'Text Window'
```

### Setup Only

If you prefer to run the `platypus` command manually in later steps:

```yaml
steps:
  - uses: actions/checkout@v4
  
  - name: Install Platypus
    uses: sveinbjornt/action-platypus@v1
    with:
      version: '5.5.0'
      
  - name: Run Platypus
    run: |
      platypus -a 'MyApp' -o 'Text Window' myscript.sh MyApp.app
```

## Inputs

| Input | Description | Default |
|Path|---|---|
| `script` | Path to the script to be bundled. If provided, the action will run the build process. | `(none)` |
| `name` | Name of the application. | `(none)` |
| `output` | Path for the generated application bundle. | `MyApp.app` |
| `interface` | Interface type (e.g., `Text Window`, `Progress Bar`, `None`, `Web View`, `Status Menu`, `Droplet`). | `(none)` |
| `identifier` | Bundle identifier (e.g., `org.example.myapp`). | `(none)` |
| `author` | Name of the author. | `(none)` |
| `appIcon` | Path to an `.icns` file for the application icon. | `(none)` |
| `interpreter` | Path to the interpreter (e.g., `/usr/bin/python3`). | `(none)` |
| `appVersion` | Version string for the application. | `(none)` |
| `bundledFiles` | Files to bundle with the app. Can be comma-separated or multiline. | `(none)` |
| `optimizeNib` | Strip the bundled application nib file to reduce size. | `false` |
| `overwrite` | Overwrite existing files at destination. | `true` |
| `version` | The version of Platypus to install. | `5.5.0` |
| `args` | Additional arguments to pass to the `platypus` command. | `(none)` |

## Example: Bundling Files

```yaml
- name: Build with Bundled Files
  uses: sveinbjornt/action-platypus@v1
  with:
    script: 'main.py'
    name: 'Python App'
    bundledFiles: |
      data.json
      assets/logo.png
    interpreter: '/usr/bin/python3'
```

## License

This action is available under the BSD-3-Clause license.
