# testscript: the bad parts

Note: this is not a critique of testscript, which I have used and continue to use with satisfection. It is, instead, a discussion starting point, in hope of finding –when fitting– workarounds, patches, or explanations to convert any such point into an asset.

## Comments as stage indicators

A comment acts as stage indicator rather than simply a comment. This is convenient, because the stages can be clearly indicated, but it is also cumbersome, because it hampers our ability of setting comments for test readability.

## Verbosity is all or nothing

When running the test with `-v`, every detail of the test is displayed –and the output is HUGE!–. There is no middle ground.

## Custom conditions are all in a single function

While custom commands are defined with a map of functions, custom conditions are tied to a single function, which should then do the parsing of the argument and define which condition we are dealing with. It's an unnecessary delegation that increases the user's burden of code.

## `testscript` is not a separate library, but comes within `go-internal`

If we want to use `testscript`, we need to import `go-internal`, which includes many libraries that might not be of interest to the user. The same burden applies to whoever wants to contribute or modify `testscript`: we need to clone the whole repo.

## `txtar` is implemented within `go/tools` and `go-internal`

`testscript` uses `txtar`, which can be imported through at least two different paths.

## Testing the application flags may clash with `go test` flags

If we run `appname -h`, we cannot expect a fixed amount of text in return, as that flag will trigger `go test -h` and show all its options.

## Repeating tasks must be explicit (there are no functions or file inclusion)

There is no easy way of repeating a set of tasks, other than writing them manually over and over. For example, after a run we may want to check that no errors were written to a log file, or that a particular file has or hasn't been created.
Possible workaround: using custom commands.

## No loops

If a check requires multiple runs with different parameters, we need to write them down explicitly.

## Limited usability of variables

Let's say your tool depends on an external entity, such as a database version or a git tag: you can use environment variables only in certain places, but not within the expected result.
Limited workaround: using `cmpenv`.




