# ClimbingOutOfTheTarPit
Resources for becoming a better programmer.

# Rationale

"This code is hard to follow."

"I fixed one bug and several new bugs appeared."

"Since surpassing X lines of code, our velocity is terrible.  Implementing even a trivial change is too expensive."

What is going on?  Things were going great when this software project was small, and then slowly everything fell apart.  What happened?

You need better tools.  Better practices, conventions, and higher levels of abstraction.

It is time for you to climb [out of the tar pit](http://shaffner.us/cs/papers/tarpit.pdf).

## Resources

### "Out of the Tar Pit" by Ben Moseley and Peter Marks

* [Paper](http://shaffner.us/cs/papers/tarpit.pdf)

### "Enemy of the State" by Justin Spahr-Summers ([2014 Functional Swift Conference](http://2014.funswiftconf.com/))

* [Video](http://2014.funswiftconf.com/speakers/justin.html)
* [Slides](https://github.com/jspahrsummers/enemy-of-the-state/tree/funswiftconf-2014)

Ideas:

* Doing what comes easy (imperative programming) leads to mutating state
* Mutating state leads to complexity
* Complexity is what makes writing software hard
* Simplicity is having a smaller number of concepts to worry about
* Complexity is the opposite of simplicity
* Essential complexity vs incidental complexity
* Increasing state increases complexity exponentially
* (Mutable) State is hard to reason about, because it changes over time
* Some amount of state is unavoidable, but you should minimize it
* Three techniques for reducing state:
  * Use immutable value types (rather than mutable reference types)
    * In Swift, this means Struct and Enum
    * Notion of values vs variables (the variable changes to take a new immutable value)
    * Immutable values have advantages (predictable and thread safe)
  * Write methods which are purely functional
    * Must not have *observable* side-effects
    * Pure functions are easier to test
  * Isolation
    * When you can't use immutable values and pure functions, isolate what is left
    * Single responsibility principle, Separation of concerns
    * Stateless core, stateful shell
      * e.g. Model-View-ViewModel (MVVM)

