# LINQ Voorbeelden

Omdat `List` de `IEnumerable`-interface implementeert, kan je i.p.v.

```
List<int> getallen = new List<int>() { 10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 1, 1 };
```

dit doen:

```
IEnumerable<int> getallen = new List<int>() { 10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 1, 1 };
```

Eens je daarna de `System.Linq`-namespace include, kan je dankzij extension methods
allerlei methods gebruiken:

```
getallen.Skip(3).Take(2).Sum();
getallen.Take(3).Average();
getallen.Reverse().Skip2().Max();
getallen.Take(5).Reverse<int>().Min();
```

Je kan bovendien gebruik maken van *method chaining* omdat deze methods telkens
de nieuwe collectie returnen.
(Methods zoals `Sum` en `Max` returnen uiteraard een getal.)

> Omdat er ook een `Reverse`-method bestaat binnen `System.Collections.Generic.List`
moet je hier wel het onderscheid maken en in dit geval `Reverse<int>` gebruiken!

