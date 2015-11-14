# Meeting 1 Questions

* What are judgments / objects of knowledge?
* What are proposition and truth judgments?
* What is constructive logic?
* What are the logical connectives for propositions in constructive logic?
* What are formation rules for propositions in constructive logic?
* What are introduction and elimination rules for propositions in constructive logic w.r.t. to truth?
* What is simple type theory?
* What is the type judgment (i.e. a : A)?
* What are the meanings of this judgment?

  * (a : A) => a is a proof of the proposition A?

  * (a : A) => a is a program of the type A?

  * (a : A) => a is a point in the synthetic topological space A?

  * Does the so-called 'Rosetta Stone' suggest other meanings for this judgment?

* What are the formation, introduction and elimination rules for types in simple type theory?

* What is the lambda calculus? How is it related to these chapters?

  * What are proof trees?

  * What are the (syntactic) formation rules for terms in the lambda calculus?

  * What is variable binding?

  * What is capture-avoiding substitution?

* What is the principle of structural induction?

* What are abstract syntax trees? 

  * Leaves vs. inner nodes: Are num[] operators leaves?

    * Talking of Num[x] at the moment - the thing I noticed/felt was that they were required to turn the numbers into Exps, so they could be used in the Exps that required Exps as arguments. No? It reminded me of wrapping numbers in an Expr ADT in Haskell, etc.

    * It's similar, but the mechanism of "turning numbers into ASTs" won't be anything we study, so it's better to just pretend it's a magic exogenous thing. We'll later learn how to implement it very nicely, though

* What are abstract binding trees?

  * How do abstract binding trees provide a form of capture-avoiding substitution?

  * ASTs are really common. Is the ABT just a PFPL concept, or do we encounter them in other work?()

  * What are examples of abstractors which simultaneously bind more than one variable? What does this mean with respect to α-equivalence?

  * From an abstract perspective, the abt `o(x y. x)` is such an example binding two variables (though referencing only one). The abt `o(a b. a)` is alpha-equivalent, the abt `o(x y. y)` is not.

  * What would an implementation for abstract binding trees look like (discuss the Standard ML implementation from Carnegie Mellon University)?

  * What is higher-order abstract syntax, e.g. as seen in the Twelf programming language? ()()()

  * I'd really like to see an answer to this from someone with Twelf experience! I'll spin it up on the group.

  * What are Jon Sterling and Darin Morrison currently working on for their upcoming paper 'Syntax and Semantics for Abstract Binding Trees'?

    * I'm happy to discuss if, but I need to be invited to the call first in order to talk. -- jon

  * Are name conflicts/renamings a real concern when implementing ABTs? It seems to me that a variable is uniquely identified by the scope where it's defined (e.g. "third argument to function f"). It seems like a problem that does not exist in practice. I guess you just answered this with de Bruijn indices.

  * Wasn't there also a recent publication that provided something similar to De Bruijn indices, but without some of the downsides? I think it was on LTU a few months back (found it: https://pchiusano.github.io/2014-06-20/simple-debruijn-alternative.html, actual paper here: http://www.cse.chalmers.se/~emax/documents/axelsson2013using.pdf). I can't really judge for myself how relevant this is.

    * The big trick to the Axelsson and Claessen method is that it lets you use functions in your implementation language as bindings in the object language. It does so by trickily examining the body of the abstractor and finding a variable assured to be fresh for it. The result is a method that's, I think, called de Bruijn "levels", but I'm not so sure there.

  * Is there a difference between the "sorts that divide ast's into syntactic categories (p. 4)" and the types of terms, or are they effectively synonyms in this context? If so, what's the significance of opting for "sort" here? ()

    * Maybe the best way to think of this is that "term" and "type" are themselves sorts... (?)

    * Ah. So it's a meta language level thing?

    * I wouldn't really say that -- it's more like, while types say something about the static semantics of a program, sorts are really only talking about the syntax of some (possibly totally meaningless) language. At least, that's how I understand it.

    * Perhaps this link is useful: http://cstheory.stackexchange.com/questions/18306/difference-between-types-and-sorts ()

* How do we join the meeting? 

  * Go to: https://plus.google.com/u/0/events/c6emnjn3h5ha7gnqj4q3pcbulf4

  * Is there an in-hangout chat?  Because there should be! ()

  * There is a sort of chat at https://plus.google.com/u/0/events/c6emnjn3h5ha7gnqj4q3pcbulf4 as in we can write comments and they show up in real time

  * If not, can we (should we?) settle on a standard alternative (like irc or google chat or something) to add this in along side?

  * There is ##typetheory on freenode, which has been around for a while. (It's specifically for this study group, I believe.) You're welcome to join :)

  * Perhaps Twitch? They have a constant chat stream with multiple people talking live.

  * Oh yea there is an IRC https://www.irccloud.com/#!/ircs://irc.freenode.net:6697/%23%23typetheory

  * Could you guys be in the chat or something, there's a weak feedback loop between presenters and people watching

* Why does Harper start with ASTs and ABTs instead of discussing type theory in general and situating it, explicating, and motivating it in detail? Is it assumed that the reader will already be well versed in type theory?

  * Harper tries to get all of the machinery out of the way in the first chapter. This leads to the book being pretty impenetrable if you don't read the next few chapters and then return back to the first chapter as a reference.

  * Harper mentions several times (Preface, etc) that the first chapter is best skimmed and returned to later as a reference. Placing it first makes it a conveniently-placed reference as you read the rest of the book. Maybe Chapter 1 should have been called "Reference Material."

  * Is this because one cannot really address the nature and importance of type theory without reference to ASTs/ABTs? Or just that this is the particular angle he is taking, because of its utility in PL theory etc?

    * You cannot define a type theory or PL until you have a theory of syntax and binding; type theories themselves can play this role, but ABTs were chosen instead because they are simpler than type theory (and readers aren't expected to have knowledge of type theory yet).

* For question 2.5(Chapter 2), it says "the size of such a representation is logarithmic, rather than linear, in the natural number it represents". What does "size" mean here?

  * "size" here means basically "number of nodes in the AST tree".