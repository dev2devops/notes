#GoLang 
### The blank identifier in multiple assignment

The use of a blank identifier in a `for` `range` loop is a special case of a general situation: multiple assignment.

If an assignment requires multiple values on the left side, but one of the values will not be used by the program, a blank identifier on the left-hand-side of the assignment avoids the need to create a dummy variable and makes it clear that the value is to be discarded. For instance, when calling a function that returns a value and an error, but only the error is important, use the blank identifier to discard the irrelevant value.

if _, err := os.Stat(path); os.IsNotExist(err) {
	fmt.Printf("%s does not exist\n", path)
}

Occasionally you'll see code that discards the error value in order to ignore the error; this is terrible practice. Always check error returns; they're provided for a reason.

// Bad! This code will crash if path does not exist.
fi, _ := os.Stat(path)
if fi.IsDir() {
    fmt.Printf("%s is a directory\n", path)
}