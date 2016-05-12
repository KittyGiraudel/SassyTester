# SassyTester

SassyTester is a minimalistic function tester in Sass. Read [API documentation](http://hugogiraudel.com/SassyTester/).

## Installation

With Eyeglass (through npm):

```
npm install sassytester
```

## Usage

### 1. Create a function

Have a function you want to test.

```scss
@function add($a, $b) {
  @return ($a + $b);
}
```

### 2. Write tests

Writing tests is as simple as creating a Sass map where the key is the function input(s) (thanks to the ability to have lists as keys), and the value is the expected output.

If we want to run 5 tests on our `add` function, we might create a map like this for instance.

```scss
$tests-add: (
  (0, 1): 1,
  (1, 4): 5,
  (2, 3): 5,
  (3, 1): 4,
  (4, 0): 4,
);
```

### 3. Run tests

```scss
@include run(test('add', $tests-add));
```

Result:

```
Started tests for function `add`
----------
Test 1 out of 5... ✔
Test 2 out of 5... ✔
Test 3 out of 5... ✔
Test 4 out of 5... ✔
Test 5 out of 5... ✔
----------
Finished: 0 test(s) failing out of 5
```
