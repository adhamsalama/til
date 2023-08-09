```py
funcs = []
for i in range(3):
  funcs.append(lambda: print(i))
for f in funcs:
  f() # prints 2, 2, 2 not 0, 1, 2
JavaScript is the opposite.
```



https://stackoverflow.com/questions/3431676/creating-functions-or-lambdas-in-a-loop-or-comprehension
