# KatchJS
A minimal testing framework inspired by CatchCpp.

It consists of a single very small pure JS script and it is so simple that it can be learned in under a minute.

## How to use
1. Setup your test suite inside a function.
2. Call RUN_KATCH(yourTestSuiteHere).

```javascript
function testSuite()
{
	//Notice that assertions are inside quotes!
	CHECK(`2 + 2`, `2 * 2`);
	CHECK(`!(!true)`)
	CHECK(`"this"`, `'this'`);

	CHECK_THROWS(`functionThatThrows()`);

	CHECK_NOTHROW(`functionThatDoesntThrow()`);
	//...
}

RUN_KATCH(testSuite);
```

There are three test clauses:

1. CHECK -> Asserts equality of two things
2. CHECK_THROWS -> Asserts that a given function (or statement) throws
3. CHECK_NOTHROW -> Asserts that a given function (or statement) doesn't throw

As Katch uses eval to do his thing inside the hood, you **_MUST use assertions in string form_** and javascript makes it very easy to do so with the backtick (\`\`) notation, specially if you need to use strings inside assertions. 
Results are printed to the console.

```javascript
//There are two versions of the CHECK assertion:
//1. One with two arguments, used to compare non boolean values, like strings, references, numbers, and so on
//2. One with a single argument where it expects a boolean value

CHECK(lhs, rhs); //Two argument version
				 //On failure it prints to the console: 
			     //"Test number ??, 'CHECK(lhs, rhs)' FAILED!
				 //Failed with: 'lhs === rhs'"

CHECK(bool); //Single argument version
	         //On failure it prints to the console: 
			 //"Test number ??, 'CHECK(lhs, true)' FAILED!
			 //Failed with: 'lhs === true'"			 

CHECK_THROWS(assertion); //On failure it prints to the console:
 						 //"Test number ??, "CHECK_NOTHROW(assertion)"\n 
 						 //FAILED with exception: exceptionString"

CHECK_NOTHROW(assertion); //On failure it prints to the console:
						  //"Test number ??, "CHECK_THROWS(assertion)" FAILED!`

```
