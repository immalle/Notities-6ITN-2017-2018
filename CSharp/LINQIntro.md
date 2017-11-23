# LINQ

- LINQ = Language Integrated Query
- Vanaf C# 3.0
- Geïmplementeerd dankzij *Extension methods* (Zie [Extension methods](ExtensionMethods.md))
- Ondersteunen *query syntax* (SQL-achtig) en *fluent syntax* (method chaining)
- Intern wordt steeds gewerkt met *fluent syntax*

# Namespace

Vergeet niet om de LINQ-namespace te includen:

```
using System.Linq;
```

## Enkele extension methods uit System.Linq (fluent syntax)

> Fluent syntax duidt op de mogelijk om de methods te *chainen*, b.v.
> `numbers.Take(3).Reverse()`

- `Reverse()` geeft een collectie in omgekeerde volgorde
- `Take(3)` geeft de eerste 3 elementen v.e. collectie
- `First()` geeft het eerste element v.e. collectie
- `Last()` geeft het laatste element v.e. collectie
- `Skip(2)` geeft een collectie zonder de eerste 2 elementen
- `Min()` geeft het kleinste element v.e. collectie
- `Max()` geeft het hoogste element v.e. collectie
- `Concat(...)` plakt 2 collecties aan elkaar
- `Union(...)` plakt 2 collecties aan elkaar zonder dubbele elementen

## Extension methods zijn niet onmiddellijk zichtbaar als dusdanig

Je kan dus C#-code schrijven waarbij het niet onmiddellijk duidelijk is
dat je LINQ gebruikt, b.v.:

```
var getallen = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9 };

Console.WriteLine("Grootste getal: " + getallen.Max());
Console.WriteLine("Kleinste getal: " + getallen.Min());
```

De `.Max()`- en `.Min()`-methods zijn extension methods uit `System.Linq`
en horen dus niet bij `List`. Ze zijn gedefinieerd voor alle `IEnumerable`'s.
`List` implementeer de `IEnumerable` interface en dus kunnen deze methods
gebruikt worden.
