# ClimbingOutOfTheTarPit
Resources for becoming a better programmer.

# Rationale

"This code is a bunch of spaghetti."

"I fixed one bug and several new bugs appeared."

"I don't like copy/paste coding, but I don't see any other way to express this idea."

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


### "Protocol-Oriented Programming in Swift" by Dave Abrahams ([WWDC 2015](https://developer.apple.com/videos/wwdc2015/))

  * [Video](https://www.youtube.com/watch?v=g2LwFZatfTI)
  * [WWDC Resources Page](https://developer.apple.com/videos/play/wwdc2015-408/)

Ideas:

* Don't use superclasses to represent abstraction (use protocols)
* Default to using a protocol (instead of a class) whenever you can
* Use a class when...
  * Copying or comparing instances is problematic / doesn't make sense
    * Value types get copied impicitly, so if that isn't workable then you need to use a reference type (e.g. a class)
  * You need control over the instance lifetime
    * Because value types are copied implicitly, their lifetime is often out of your control, so use a reference type if that's a problem.
  * Instances are just "sinks"
    * (I don't yet fully understand this point.  Is the reasoning that it isn't worth the trouble in this case?)
  * When limited by legacy code (e.g. a framework expects an NSObject subclass)

### "Functional Core, Imperative Shell" by Gary Bernhardt

* [Video](https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell) (this video must be purchased as part of Season 4 of [Destroy All Software](https://www.destroyallsoftware.com/screencasts/catalog))

Ideas:
* Achieve mutable state while remaining functional by returning a mutated copy of self upon mutation
* Isolate pure functional code into a core, wrap it with imperative shell
* Functional core is tested (without using mocks or stubs)
* Imperative shell is not tested (at all)
  * Dangerous?  Minimize the danger via:
    * Minimizing the number of conditionals in the imperative shell

### "Boundaries" by Gary Bernhardt
* [Video](https://www.destroyallsoftware.com/talks/boundaries) (SCNA 2012)
* [Video](https://www.youtube.com/watch?v=yTkzNHF6rMs) (RubyConf 2012)
* [Video](http://pyvideo.org/video/1670/boundaries) (PyCon 2013)

### "The Functional Way" by Natasha Murashev
* [Video](https://www.youtube.com/watch?v=tohEJSq9gds) (2014 Functional Swift Conference)
* [Conference talk page](http://2014.funswiftconf.com/speakers/natasha.html)

### Backlog

* "Advanced Swift" by John McCall and Dave Abrahams
  * [Video](https://www.youtube.com/watch?v=g44U1937o0g)
* "Simplicity Matters" by Rich Hickey
  * [Video](https://www.youtube.com/watch?v=rI8tNMsozo0)
* "The Value of Values" by Rich Hickey
  * [Video](https://www.youtube.com/watch?v=-6BsiVyC1kM)
* "Simple Made Easy" by Rich Hickey
  * [Presentation](http://www.infoq.com/presentations/Simple-Made-Easy) (requires Flash)
* "Pattern: Backends For Frontends" by Sam Newman
  * [Website](http://samnewman.io/patterns/architectural/bff/)
* "Integration Tests Are a Scam" by J.B. Rainsberger
  * [Presentation](http://www.infoq.com/presentations/integration-tests-scam)
  * [Video](https://vimeo.com/80533536)
* "Less: The Path to Better Design" by Sandi Metz
  * [Video](https://vimeo.com/53154357)
* "Williams, Master of the 'Come From'" by Reginald "raganwald" Braithwaite
  * [Article](https://github.com/raganwald-deprecated/homoiconic/blob/master/2011/11/COMEFROM.md)
* "Javascript Combinators" by Reginald "raganwald" Braithwaite
  * [Video](https://vimeo.com/97408202) (NDC 2014)
* "Functional Testing" by Brian Gesiak
  * [Video](http://2014.funswiftconf.com/speakers/brian.html) (2014 Functional Swift Conference)
* [How to fix a bad user interface](https://scotthurff.com/posts/why-your-user-interface-is-awkward-youre-ignoring-the-ui-stack?utm_campaign=iOS%2BDev%2BWeekly&utm_medium=email&utm_source=iOS_Dev_Weekly_Issue_226) by Scott Hurff
* [Destory All Software](https://www.destroyallsoftware.com/screencasts/catalog)
* https://gist.github.com/jhrr/7368923
* [SCNA 2012 videos](https://vimeo.com/search?q=scna+2012)
* [SCNA 2013 videos](https://vimeo.com/search?q=scna+2013)
* https://gist.github.com/JaviLorbada/4a7bd6129275ebefd5a6
* http://www.jonathanholloway.co.uk/thesis/MPhilThesis.pdf
* https://github.com/typelift
* http://www.drewag.me/posts/practical-use-for-curried-functions-in-swift
* http://www.introtorx.com/
* "OMeta: an Object-Oriented Language for Pattern Matching" [Paper](http://tinlizzie.org/~awarth/papers/dls07.pdf)
* "Real World Haskell" [Book](http://book.realworldhaskell.org/read/)
* https://vimeo.com/search?q=Reginald+Braithwaite
* "Less - The Path to Better Design" [Video](https://vimeo.com/53154357)
* "The Clean Architecture" by Robert Martin [Article](http://blog.8thlight.com/uncle-bob/2012/08/13/the-clean-architecture.html)
