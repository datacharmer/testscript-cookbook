# testscript-cookbook plan

This repository aims at collecting examples, methods, explanations, and related techniques that are not available through [`testscript` official documentation](https//github.com/rogpeppe/go-internal).

There are three main goals:

1. Document the basic usage of `testscript`, even though most of such usage is already covered in the [regular documentation](https//github.com/rogpeppe/go-internal), [articles](https://bitfieldconsulting.com/search?q=testscript), and [a book](https://bitfieldconsulting.com/books/tests).
2. Document the advanced usage of `testscript`, with emphasis on custom commands and conditions, which are only minimally defined in the documentation.
3. Show how to use `tesctscript` to test custom build operations (e.g. a build that includes git tags information).

And two optional ones
4. Show how to implement repetitive tests using templates.
5. Show how to run tests with the testscript tool (without running `go test`).

The above goals will be achieved by testing the development of a companion repository ([github.com/datacharmer/cliptool](https://github.com/datacharmer/cliptool))
