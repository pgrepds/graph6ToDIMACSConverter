# graph6ToDIMACSConverter
A simple tool based on SageMath for converting the graph6 file format to [DIMACS](https://github.com/akinanop/mvl-solver/wiki/DIMACS-Graph-Format).

Let `DrK` be a graph6 string (this is the house graph).

We can convert it to DIMACS as follows

```python
result=convert("DrK")
print(result)
```

which yields to

```python
p edge 5 6
e 0 1
e 0 2
e 1 3
e 2 3
e 2 4
e 3 4
```

If we want to provide a description (the 'c' line), we can achieve this as follows.

```python
result=convert("DrK", "This is an optional description")
print(result)
```

which yields to

```python
c This is an optional description
p edge 5 6
e 0 1
e 0 2
e 1 3
e 2 3
e 2 4
e 3 4
```

I have added a convenient function in order to convert a given graph6 file directly to a DIMACS file.

Assume that we have a graph6 file named "house.g6" whose content looks as follows.

```python
DrK
```

Then, we can convert the file directly using the above function as follows, whereby the file is located in the same directory. If it is not, then we need to provide the full path.

```python
convertGraph6FileToDimacsFile(pathToGraph6File, pathToDimacsFile)
```

The output is a DIAMCS file containing the content given above. If you have a huge g6 file with multiple graphs, then you can easily read this file line by line and convert each graph using the above functions.

Notice that the above does not work if the optional graph6 header `>>graph6<<` is provided. If that is the case, then we need to do some preprocessing first (which is not very complicated).
