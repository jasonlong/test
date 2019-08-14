```yaml
jobs:
  test:
    name: Test on node ${{ matrix.node_version }} and ${{ matrix.os }} and let's make this line super long so that it needs to scroll horizontally
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        node_version: [8, 10, 12]
        os: [ubuntu-latest, windows-latest, macOS-latest]

    steps:
    - uses: actions/checkout@v1
    - name: Use Node.js ${{ matrix.node_version }}
      uses: actions/setup-node@v1
      with:
        version: ${{ matrix.node_version }}

    - name: npm install, build and test
      run: |
        npm install
        npm run build --if-present
        npm test
```
