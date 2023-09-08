# Getting Started with Artillery

Performance testing using [artillery](artillery.io)

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
- **Get request**: see the `api-get-jsonplaceholder.yml` script
- **Post request**: see the `api-post-booker.yml` script. Constructs the json payload for the request. Shows how to capture multiple values from the same json response
- **A sample load scenario**: see the `getting-started-first-test.yml` script

### Run tests
Run scripts in bash or PowerShell. I prefer working in a bash terminal, then:

Run any script, and see full detail printed out on the terminal:

`artillery run api-get-jsonplaceholder.yml`

You will see a full detail of perf metrics from this run printed on the console.

To 'test' run a script, i.e. ignoring the loading scenarios in the script, you can run that script as follows:

```sh
artillery quick -c 1 -n 1 getting-started-first-test.yml

# alternatively, you can also directly hit an api directly to see if it works before coding it into a script

artillery quick -c 1 -n 1 https://httpbin.org/get

# or, to suppress report output, but see that the content returns
DEBUG=http:response artillery quick -c 1 -n 1 https://jsonplaceholder.typicode.com/todos/1 --quiet
```

### Debugging and Console output
To skip all that detail and only see log outputs from the script:

`artillery run api-get-jsonplaceholder.yml --quiet`

Debug execution; I prefer to suppress the report output when I am debugging to see content, however, when running the test, remove the `--quiet` flag:

```sh
# http header info
DEBUG=http artillery run api-get-jsonplaceholder.yml --quiet

# response details:
DEBUG=http:response artillery run api-get-jsonplaceholder.yml --quiet

# capture details
DEBUG=http:capture artillery run api-get-jsonplaceholder.yml --quiet

```

## References
- [Getting Started](https://www.artillery.io/docs/get-started/first-test)
- [Understanding components of a test script](https://www.artillery.io/docs/reference/test-script)
- [Working with APIs](https://www.artillery.io/docs/reference/engines/http)
