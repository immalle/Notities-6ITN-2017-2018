# Dictionaries

Dictionaries staan bekend onder verschillende namen:

- Maps
- HashMaps
- Key-Value-datastructuur
- ...

Het is een soort *mapping* tussen een **key** en een **value**, wat erg handig
kan zijn in bepaalde scenario's.

# Aanmaken

Een mapping tussen woorden en hoe vaak ze voorkomen:

```C#
Dictionary<string, int> woordTeller = new Dictionary<string, int>();
```

Een mapping tussen een `Persoon` en een URL van zijn/haar website:

```C#
class Persoon {
    string achternaam;
    string voornaam;
}

Dictionary<Persoon, string> websiteURLs = new Dictionary<string, string>();
```

# Element toevoegen

Stel dat we het object `jos` hebben:

```
Persoon jos = new Persoon();
jos.Voornaam = "Jos";
jos.Achternaam = "Bosmans";
```

Dan kunnen we een element toevoegen op deze manier:

```
websiteURLs[jos] = "http://github.com";
```

Of op deze manier:

```
websiteURLs.Add(jos, "http://github.com");
```

Het valt daarbij op dat:

- de Key een `Persoon`-object is
- de Value een `string` is

# Itereren over Keys of Values

Itereren over een `Dictionary` komt minder vaak voor dan bij een `List`.
Dat komt omdat we meestal gebruik maken van de *mapping*.


Hiermee printen we de value (de URL-string) die bij de key (het Persoon-object) hoort:

```
Console.WriteLine(websiteURLs[jos]);
```

Hiermee geven we de value die bij de key hoort een andere waarde:

```
websiteURLs[jos] = "http://gitter.im";
```

Als je toch wil itereren over een `Dictionary` met `foreach`, krijg je een `KeyValuePair` terug:

```
foreach(var kv in websiteURLs) {
	Console.WriteLine(kv.Key);
	Console.WriteLine(kv.Value);
}
```

Het kan soms nuttig zijn om enkel over de keys te itereren.
Dan kan je b.v. best de keys eerst in een lijst zetten.

Zie https://www.dotnetperls.com/dictionary.

# Achtergrondinformatie

Achter de schermen maakt een dictionary gebruik van (cryptografische) hashes.

Dit zorgt ervoor dat een Dictionary geoptimaliseerd is om snel op basis van key te zoeken.

Met een lijst van b.v. 1000 elementen, moet je om te zoeken elk element inlezen en controleren
of je het gezochte gevonden hebt. Bij een Dictionary zorgt de hash ervoor dat veel sneller de
juiste waarde gevonden wordt, zonder heel de Dictionary te moeten doorzoeken.

Dictionaries zijn dan ook sneller dan Lists om in te zoeken maar trager om elementen aan toe te voegen.

# Voorbeelden

- https://dotnetfiddle.net/TEWeEX : woorden tellen 1 (met meerdere split-chars)
- https://dotnetfiddle.net/5Ktqsg : woorden tellen 2 (in aparte method)

