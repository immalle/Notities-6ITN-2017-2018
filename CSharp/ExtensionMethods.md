# Extension methods

Extension methods zijn een manier om een class uit te breiden met extra methods
zonder hiervoor de class zelf te moeten aanpassen of overerven.

## In het kort

Een extension method maak je door een static class te definieren waarin je een static
een static method definieerd waarvan de eerste parameter `this` bevat en het type van
het object dat je wil extenden (uitbreiden).

## Uitgebreid voorbeeld

Met Extension methods kan je een bestaande class uitbreiden.

> Extension methods worden dus typisch in een andere namespace/package gemaakt.
> Je moet dat package dus expliciet includen met `using`.
> Een typisch voorbeeld is `System.Linq`.

Ze zijn als volgt te herkennen:

- de eerste parameter bevat `this` en de class die wordt uitgebreid
- de extension methods zijn `static`
- de extension methods behoren tot een `static class`

B.v. het uitbreiden v.d. bestaand `System.String`-class:

```
namespace ExtensionMethods
{
    public static class MyExtensions
    {
        public static int WordCount(this String str)
        {
            return str.Split(new char[] { ' ', '.', '?' }, 
                             StringSplitOptions.RemoveEmptyEntries).Length;
        }
    }
}
```

Opmerkingen:

- Extension methods zijn geen echte member-methods: de compiler zet ze om naar static methods.
  Je kan dan ook geen private variabelen benaderen via extension methods.
- Als er al een gewone (instantie)-method bestaat met dezelfde naam en signatuur,
  zal deze de voorkeur hebben.
- In VS gebruikt men als icoon voor extension methods hetzelfde kubus-icoontje als voor
  gewone methods maar dan met een naar onder wijzende pijl.

# Further reading

- https://msdn.microsoft.com/en-us/library/bb383977.aspx
- https://www.dotnetperls.com/extension

