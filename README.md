# Platypus GitHub Action

## Work in progress!

This action installs [Platypus](https://sveinbjorn.org/platypus), a developer tool that creates native macOS applications from command line scripts (Shell, Python, Perl, Ruby, PHP, JavaScript, etc.).

This action downloads and sets up the `platypus` command line tool so you can use it in your workflow.

## Usage

```yaml
steps:
  - uses: actions/checkout@v4
  
  - name: Install Platypus
    uses: sveinbjornt/action-platypus@v1
    with:
      version: '5.5.0'
      
  - name: Build App
    run: |
      platypus -a 'MyApp' -o 'Text Window' myscript.sh MyApp.app
```

## Inputs

| Input | Description | Default |
|---|---|---|
| `version` | The version of Platypus to install. | `5.5.0` |

## License

This action is available under the BSD-3-Clause license.
