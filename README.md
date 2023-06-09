# Family Relationships

This is a Prolog code that defines various facts and rules related to family relationships. It allows you to query relationships such as father, mother, grandfather, grandmother, sister, aunt, brother, uncle, and ancestor based on the provided facts.

## Facts

The following facts are defined:

```
male(jack).
male(oliver).
male(ali).
male(james).
male(simon).
male(harry).
female(helen).
female(sophie).
female(jess).
female(lily).
```

```
parent_of(jack,jess).
parent_of(jack,lily).
parent_of(helen, jess).
parent_of(helen, lily).
parent_of(oliver,james).
parent_of(sophie, james).
parent_of(jess, simon).
parent_of(ali, simon).
parent_of(lily, harry).
parent_of(james, harry).
```

## Rules

The following rules are defined:

```
father_of(X,Y):- male(X),
    parent_of(X,Y).
```

```
mother_of(X,Y):- female(X),
    parent_of(X,Y).
```

```
grandfather_of(X,Y):- male(X),
   parent_of(X,Y), male(X).
```

```
grandmother_of(X,Y):- female(X),
    parent_of(X,Z),
    parent_of(Z,Y).
```

```
sister_of(X,Y):- female(X),
    father_of(F, Y), father_of(F,X), X \= Y.
```

```
sister_of(X,Y):- female(X),
    mother_of(M, Y), mother_of(M,X), X \= Y.
```

```
aunt_of(X,Y):- female(X),
    parent_of(Z,Y), sister_of(Z,X),!.
```

```
brother_of(X,Y):- male(X),
    father_of(F, Y), father_of(F,X), X \= Y.
```

```
brother_of(X,Y):- male(X),
    mother_of(M, Y), mother_of(M,X), X \= Y.
```

```
uncle_of(X,Y):-
    parent_of(Z,Y), brother_of(Z,X).
```

```
ancestor_of(X,Y):- parent_of(X,Y).
ancestor_of(X,Y):- parent_of(X,Z),
    ancestor_of(Z,Y).
```

Feel free to modify the facts and rules or add more relationships as needed.
