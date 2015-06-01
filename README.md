# SassyTester

SassyTester is a minimalistic function tester in Sass. Read [API documentation](http://hugogiraudel.com/SassyTester/).

## 1. Create a function

Have a function you want to test.

```scss
@function double($value) {
  @return $value * 2;
}
```

## 2. Write tests

Writing tests is as simple as creating a Sass map where the key is the function input, and the value is the expected output. If we want to run 5 tests on our `double` function, we might create a map like this for instance.

```scss
$tests-double: (
  0: 0,
  1: 2,
  2: 4,
  3: 6,
  4: 8,
);
```

## 3. Run tests

```scss
@include run(test('double', $tests-double));
```

Result:

```
Started tests for function `double`
----------
Test 1 out of 5... ✔
Test 2 out of 5... ✔
Test 3 out of 5... ✔
Test 4 out of 5... ✔
Test 5 out of 5... ✔
----------
Finished: 0 test(s) failing out of 5
```

If you want the raw data, without the printing as an `@error`, you can use the result of the `test(..)` function. Indeed, the `run(..)` mixin only takes the data from the `test(..)` call, and pretty print it through `@error`. The actual testing logic happens in `test(..)`.
