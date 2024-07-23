# Basic testscript usage


## `main_test.go`

The first element needed to use `testscript` is a regular test function `TestFoo()` that invokes `testscript.Run()`.
As part of the input, we indicate a directory of scripts. The test will run all the scripts with extension `.txtar` in such directory.

```go
import (
	"testing"

	"github.com/rogpeppe/go-internal/testscript"
)

func TestFoo(t *testing.T) {
	testscript.Run(t, testscript.Params{
		Dir: "testdata",
	})
}
```

## `testdata`

The second element is one or more scripts with extension `.txtar`, located into the directory indicated in `TestFoo()`

### `testdata/first.txtar`

```
# testing the executable
exec myapp hello.text
stdout 'hello world'
! stderr .

-- hello.text --
hello world
```

### `testdata/second.txtar`

```
# testing the executable with bad input
! exec myapp hi.text
! stdout .
stderr "file not found"

-- hello.text --
hello world
```
