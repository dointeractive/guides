# Ruby Style Guide

  1. [Whitespace](#whitespace)
  2. [Syntax](#syntax)
  3. [Line breaks](#line-breaks)
  4. [Naming](#naming)
  5. [Classes](#classes)
  6. [Exceptions](#exceptions)
  7. [Strings](#strings)
  8. [Spelling and grammar](#spelling-and-grammar)
  9. [Be Consistent](#be-consistent)

## Whitespace

* Use soft-tabs with a two space-indent.
* Don't leave trailing whitespace.
* Put spaces before and after block of code or if you breaks long line
    ```Ruby
    # do
    def a
      id = 1 + 2

      records = Record.where(
        id: id,
        name: 'guide')

      records.each do |e|
        puts e
      end

      result = 5
    end

    # don't
    def b
      id = 1 + 2
      records = Record.where(
        id: id,
        name: 'guide')
      records.each do |e|
        puts e
      end
      result = 5
    end
    ```
* Use spaces around operators, after commas, colons, and semicolons and after
  `{` and before `}`.

    ```Ruby
    sum = 1 + 2
    a, b = 1, 2
    [1, 2, 3].each{ |e| puts e }
    ```
* Don't use spaces after `(`, `[` or before `]`, `)`.

    ```Ruby
    some(arg).other
    [1, 2, 3].length
    ```

## Syntax
* Prefer the Ruby 1.9 hash literal syntax where it is possible.

    ```Ruby
    # do
    hash = { foo: 1, bar: 2 }
    ```
* Don't mix the Ruby 1.9 hash syntax with hash rockets in the same hash literal. When you've got keys that are not symbols stick to the hash rockets syntax.
* Prefer `{...}` over `do...end` for single-line blocks.  Avoid using
  `{...}` for multi-line blocks (multiline chaining is always
  ugly). Always use `do...end` for "control flow" and "method
  definitions".  Avoid `do...end`
  when chaining.

    ```Ruby
    names = ["Bozhidar", "Steve", "Sarah"]

    # do
    names.each{ |name| puts name }

    # don't
    names.each do |name|
      puts name
    end

    # do
    names.select{ |name| name.start_with?("S") }.map{ |name| name.upcase }

    # don't
    names.select do |name|
      name.start_with?("S")
    end.map{ |name| name.upcase }
    ```

* Avoid `return` where not required.
* Use `||=` to initialize variables. But don't use `||=` to initialize boolean variables. (Consider what  would happen if the current value happened to be `false`.)
* Use `_` for unused block parameters.

    ```Ruby
    # do
    result = hash.map{ |_, v| v + 1 }
    # don't
    result = hash.map{ |k, v| v + 1 }
    ```

* When a method block takes only one argument, and the body consists solely of
  reading an attribute or calling one method with no arguments, use the `&:`
  shorthand.

    ```ruby
    # do
    names.map &:upcase

    # don't
    names.map{ |n| n.upcase }
    ```

## Line breaks
* Consider following examples, breaking long lines of code:

    ```ruby
    # do
    hash = {
      one: 1,
      two: 2,
      three: 3
    }

    # do
    compute_things 'arg',
      one: 1,
      two: 2

    # do
    compute_things(
      'arg_1',
      'arg_2',
      'arg_3'
    )

    # do
    attr_accessor(
      :one,
      :two,
      :three,
    )

    # don't
    hash = { one: 1,   two: 2,
             three: 3, four: 4 }

    # don't
    compute_things 'arg', one: 1,
      two: 2

    # don't
    compute_things('arg_1', 'arg_2',
      'arg_3')

    # don't
    attr_accessible :one, :two, :three,
      :four, :five
    ```

## Naming

* Use `snake_case` for methods and variables.
* Use `CamelCase` for classes and modules.  (Keep acronyms like HTTP,
  RFC, XML uppercase.)
* Use `SCREAMING_SNAKE_CASE` for other constants.
* When you choosing method and class names – take the shortest one.
* The names of predicate methods (methods that return a boolean value)
  should end in a question mark. (i.e. `Array#empty?`).
* If you don't know how to name a method or class try to ask yourself what does method do? Then simply write everything the method does. If name gets too long, then your method potentially have too much responsibilities. At the same time if you can't shortly describe what method does – you also have a problem with your design.

## Classes

* Use `def self.method` to define singleton methods.

## Exceptions
* Don't use exceptions for flow of control.

    ```Ruby
    # do
    if d.zero?
      puts "Cannot divide by 0!"
    else
      n / d
    end

    # don't
    begin
      n / d
    rescue ZeroDivisionError
      puts "Cannot divide by 0!"
    end
    ```

* Avoid rescuing the `Exception` class.

    ```Ruby
    # do
    begin
      # an exception occurs here
    rescue StandardError
      # exception handling
    end

    # don't
    begin
      # an exception occurs here
    rescue Exception
      # exception handling
    end
    ```

## Strings
* Prefer string interpolation instead of string concatenation:

    ```Ruby
    # do
    email_with_name = "#{user.name} <#{user.email}>"

    # don't
    email_with_name = user.name + ' <' + user.email + '>'
    ```
* Prefer single-quoted strings when you don't need string interpolation or special symbols such as \t, \n, ', etc.

## Spelling and grammar

Pay attention to punctuation, spelling, and grammar; it is easier to read
well-written code than badly written ones.

## Be Consistent

> If you're editing code, take a few minutes to look at the code around you and
> determine its style. If they use spaces around all their arithmetic
> operators, you should too. If their comments have little boxes of hash marks
> around them, make your comments have little boxes of hash marks around them
> too.

> The point of having style guidelines is to have a common vocabulary of coding
> so people can concentrate on what you're saying rather than on how you're
> saying it. We present global style rules here so people know the vocabulary,
> but local style is also important. If code you add to a file looks
> drastically different from the existing code around it, it throws readers out
> of their rhythm when they go to read it. Avoid this.

&mdash;[Google C++ Style Guide][google-c++]

[airbnb-javascript]: https://github.com/airbnb/javascript
[bbatsov-ruby]: https://github.com/bbatsov/ruby-style-guide
[github-ruby]: https://github.com/styleguide/ruby
