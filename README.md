# Motivations
There are no good ways of resolving a conditional to a nullish value as they resolve to a  truthy value by default. The nullish ternary will resolve the conditional to a nullish value without needing the extra syntax necessary to make this possible.

# Details
A regular ternary looks like this and solves the condition based on truthiness
``` markdown
(condition) ? expression_if_truthy : expression_if_falsey
```

The proposed nullish ternary will look like this and solves the condition based on nullishness
``` markdown
(condition) ?? expression_if_not_nullish : expression_if_nullish
```

# Current Implementations
I see no good ways of doing this in the current ECMAScript standard as they either don't account for the "else" clause or don't accomplish the task in a clean way. If I'm missing any ways that this can be done without the proposed nullish ternary please let me know.

It could be done using an AND statement with the condition referenced twice but this could be done better.
``` markdown
(condition !== null && condition !== undefined) ? expression_if_not_nullish : expression_if_nullish
```

A nullish coalescing operator could be used but wouldn't be able to evaluate the expression_if_not_nullish.
``` markdown
(condition ?? expression_if_nullish)
```

Or it could be done with a hash but this is very awkward and would assume the condition doesn't evaulate to the long_hash_value.
``` markdown
((condition ?? long_hash_value) !== long_hash_value) ? expression_if_not_nullish : expression_if_nullish
```

# Obstacles 
The reason this might not be possible is because ?? is already being used as the nullish coalescing operator while the ? did not have a previous coalescing meaning. This will prove difficult especially when trying to implement ternary chaining. Hopefully, these problems will not prove too difficult and a clean way of resolving conditionals for nullishness can be accomplished.

