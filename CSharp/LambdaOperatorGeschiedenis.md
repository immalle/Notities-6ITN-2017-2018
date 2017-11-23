## Paradigm shift naar functioneel

`List<T>` is al lang aanwezig in C#.
Hier werd een `ForEach`-method aan toegevoegd die met zogenaamde *delegates* kon werken.

Sinds LINQ is toegevoegd aan C#, zijn de LINQ extensions methods een beter manier om *functioneel* te programmeren.
De `ForEach`-method bestaat natuurlijk nog wel steeds.

De delegates werden eerst vervangen door de `Action<T>`-class.

Tegenwoordig kunnen we de **lambda operator** `=>` gebruiken.


## Vergelijk

met LINQ:

```
class Program
{
    static void Main()
    {
        List<String> names = new List<String> { "andrew", "nicole" };

        names.ForEach(s => Console.WriteLine(s));
    }
}
```

met `delegate` (verouderd!):

```
class Program {
  static void Main() {
    List<String> names = new List<String> { "andrew", "nicole" };

    names.ForEach(delegate(String s) {
      Console.WriteLine(s);
    }); 
  }
}
```

met `Action` (nieuwere variant van `delegate`):

```
using System;
using System.Collections.Generic;

class Program {
  static void Main() {
    Action<String> print = new Action<String>(Console.WriteLine);

    List<String> names = new List<String> { "andrew", "nicole" };

    names.ForEach(print); 
  }
}

```

met Action (lange versie):

```
class Program
{
    static void Main()
    {
        Action<String> print = new Action<String>(Program.Print);

        List<String> names = new List<String> { "andrew", "nicole" };

        names.ForEach(print);
    }

    static void Print(String s)
    {
        Console.WriteLine(s);
    }
}
```

Uiteindelijk is `ForEach` gedefinieerd met een `Action` als parameter.
(Dus `Action` blijft de convenience-functie.)

bron: http://stackoverflow.com/questions/371054/uses-of-action-delegate-in-c-sharp

