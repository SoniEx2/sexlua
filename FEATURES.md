Features
========

This is a list of (to-be-)implemented features.

- [ ] `Return()` function
    
    The `Return()` function is tightly coupled to the core. It allows for
    premature returns in expressions. It works like `coroutine.yield()`,
    except you cannot "resume" a `Return()`ed function.
- [x] Self-with-expression
    
    Self-with-expression is about being able to use `self:calls()` with
    index expressions, using the syntax `self:[index_expression]()`.
- [ ] ???
    
    I don't have a good name for this, but it is about being able to
    use self calls on a different object than the table containing the
    function. For example, `_G:table.insert("some object")` roughly
    translates to `_G.table.insert(_G, "some object")`.
    
    This can be combined with the above to make things like
    `_G:["_G"]["table"].insert("some object")`, which roughly translates
    to `_G["_G"]["table"].insert(_G, "some object")`.
    
