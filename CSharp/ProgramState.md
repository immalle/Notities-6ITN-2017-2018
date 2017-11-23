# Program state (en Hashmaps)


## Herhalingsoef

Maak een applicatie waarbij je : 

- in de `Main`-method een variabele aanmaakt : `var dir = @"C:\TESTDIR"`
- Je met `Directory.CreateDirectory` deze directory aanmaakt **als deze nog niet
  bestaat** (te checken met `Directory.Exists`)
- de foutmelding `Directory [{0}] bestaat al.` moet in het **geel** weergegeven
  worden als hij al bestaat
- de melding `Directory [{0}] gemaakt.` in het **groen** verschijnt
- Als `dir` leeg is (`String.Empty` of `""`) dan moet de melding `Kan directory
  niet maken: naam niet opgegeven.` in het **rood** worden weergegeven

# Versie 2 : Refactor Versie 1

Gebruik:

```
enum Status {
            NoNameGiven,
            DirMade,
            DirExists
}
```

om de 3 eind-toestanden van het programma in op te slaan.

- Maak eerst een `Status`-object: `Status programStatus;` (je moet geen `new`
  gebruiken voor een `enum`-type omdat dit, net als `struct`, een **Value-type**
  is)
- Doe de afhandeling van de *core logic* of de *business logic* eerst (de
  directories maken en checken), waarbij je `programStatus` de juiste waarde
  geeft
- Gebruik daarna `programStatus` om (in de laatste regels v.d. `Main`-method) de
  correcte foutmelding te geven a.h.v. de waarde v.d. `enum`, met `if/else` of
  beter `switch/case`

# Versie 3 : Gebruik Dictionaries ...

... om de mappings tussen te maken tussen : 

- programstatus en console-melding
- programstatus en kleur van de melding

Oplossing: https://github.com/vbrh-immalle/SharpShell/blob/eb935427bccd745b35b6ec05074c36fc3b089463/Program.cs
