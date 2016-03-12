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
- [ ] Accept more __call-ables
    
    This feature adds more support for __call-ables so you can use them
    in more stuff (xpcall's second argument, for example).
- [ ] Yieldable string.gsub() functions
    
    What if you could coroutine.yield() from inside a string.gsub()
    function? e.g. `string.gsub(s,p,function(...) return
    coroutine.yield(...) end)`
- [ ] Mangle C functions to workaround exploits
    
    Use an array and dynamically put C functions in it as they're being
    accessed. Patch OP_GETTABLE to mangle them on read.
- [x] Self-referential functions
    
    Allows a function, anonymous or otherwise, to refer to itself through `@`.
    
    Example:
    
    ```lua
    -- plain Lua
    local function f(i)
      if i == 0 then return end
      return f(i-1)
    end
    local g=f
    f=print
    g(1) -- prints 0
    -- self-referential functions
    local function f(i)
      if i == 0 then return end
      return @(i-1)
    end
    local g=f
    f=print
    g(1) -- loops once
    f(2) -- prints 2
    ```
