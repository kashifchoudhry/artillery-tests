# Getting Started with Artillery

Run artillery scripts in bash or PowerShell

**Install**

`npm install -g artillery@latest`

Check that it is installed:
```sh
npx artillery dino
# or
artillery version
```

## Usage

### Scripts explained
- **Get request**: see the `jsonplaceholder.yml` script
- **Post request**: see the `booker.yml` script. Constructs the json payload for the request. Shows how to capture multiple values from the same json response
- **A sample load scenario**: see the `getting-started-first-test.yml` script

### Run tests
Open a bash terminal, then:

Run any script, and see full detail printed out on the terminal:

`artillery run jsonplaceholder.yml`

### Debugging and Console output
To skip all that detail and only see log outputs from the script:

`artillery run jsonplaceholder.yml --quiet`

Debug execution; I prefer to suppress the report output when I am debugging to see content, however, when running the test, remove the `--quiet` flag:

```sh
# http header info
DEBUG=http artillery run jsonplaceholder.yml --quiet

# response details:
DEBUG=http:response artillery run jsonplaceholder.yml --quiet

# capture details
DEBUG=http:capture artillery run jsonplaceholder.yml --quiet

```

## References
- [Getting Started](https://www.artillery.io/docs/get-started/first-test)
- [Understanding components of a test script](https://www.artillery.io/docs/reference/test-script)
- [Working with APIs](https://www.artillery.io/docs/reference/engines/http)
