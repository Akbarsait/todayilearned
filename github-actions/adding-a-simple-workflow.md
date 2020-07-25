# Adding a simple github workflow
A simple receipe to see how github actions work. 
```yaml
on: [push]

jobs:
  build:
    name: Greetings
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run a multi-line script
      run: |
        echo Add other actions to build,
        echo test, and deploy your project.
```