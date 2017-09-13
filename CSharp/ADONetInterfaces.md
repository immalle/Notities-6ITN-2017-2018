# ADO.Net interfaces

## Inleiding

Ado.Net is de naam die gegeven wordt aan het database-framework van .Net.
Dit is het basis-framework waarop andere libraries (zoals het Entity Framework, een ORM),
gebruik van maken. Als je leert werken met ADO.Net, leer je dus de meest low-level manier
om in C# met databases te communiceren.

## ADO.Net data providers en NuGet packages

ADO.Net zit vervat in een aantal namespaces die in de standaard library zitten.

`System.Data` bevat een aantal *interfaces* (waarover later meer)

`System.Data.SqlClient` biedt ondersteuning voor Microsoft's SQL Server.

We kunnen echter ook extra libraries (via een NuGet-package) installeren, die nieuwe
namespaces toevoegen, zoals `System.Data.MySqlClient`.
Wij zullen gebruik maken van extra library die toegang verschaft tot MySQL-databases.

Er zijn minstens 2 van deze libraryes, zogenaamde *ADO.Net data providers*, voor MySQL:

- https://www.mysql.com/products/connector/ (officieel van MySQL)
- https://mysql-net.github.io/MySqlConnector/ (een recente die compatibel is met .Net core 2
en zich voornamelijk op asynchrone toegang toespitst)

Beiden zijn ook via NuGet te downloaden:

- https://www.nuget.org/packages/MySql.Data/8.0.8-dmr
- https://www.nuget.org/packages/MySqlConnector/

## OOP-ontwerp van ADO.Net

De structuur van ADO.Net is een mooi voorbeeld van object oriented design, meerbepaald
met *interfaces*.

> Oef. : Ga naar https://docs.microsoft.com/en-us/dotnet/api/?view=netcore-2.0. Je ziet
hier een volledig overzicht van de standard library van .Net Core 2.0.
Bekijk de `System.Data.*`-namespaces en lees de omschrijvingen.

`System.Data` bevat een aantal interfaces die bepalen hoe we in ADO.Net met databases
moeten werken:

- `IDbConnection` : definieert wat we met een connectie met een database kunnen doen,
  b.v. `Open()` en `Close()`
- `IDbCommand` : definieert wat een SQL-command zoals nodig heeft, zoals `CommandText`
(een SQL-statement zoals `SELECT * FROM ...`) en de methods:
    - `ExecuteNonQuery()` : om queries uit te voeren die niets returnen, zoals `INSERT ...`
    - `ExecuteScalar()` : om queries uit te voeren die 1 waarde returnen, zoals bij
      aggregatiefuncties (`SELECT COUNT(*) FROM ...`)
    - `ExecuteReader()` : om queries uit te voeren die meerdere rijen returnen

Een fabrikant van een database, kan nu deze interfaces gebruiken om **in te pluggen**
in het ADO.Net-framework, door classes te schrijven die deze interfaces implementeren.

> Vergelijk het implementeren van interfaces met het overerven van een abstract class!

In het geval van `System.Data.MySqlClient` hebben we b.v. de classes:

- `System.Data.MySqlClient.MySqlConnection` die de interface `IDbConnection` implementeert
- `System.Data.MySqlClient.MySqlCommand` die de interface `IDbCommand` implementeert

Anderzijds kunnen Microsoft's SQL server gebruiken met

- `System.Data.SqlClient.SqlConnection`
- `System.Data.SqlClient.SqlCommand`

Beide implementaties (voor MySql en Sql Server) zijn dus voor de eindgebruiker exact
hetzelfde te gebruiken, o.w.v. de voorgedefinieerde interfaces in `System.Data`.

Dit is een groot voordeel van programmeertalen die werken met **interfaces**!

# Oefeningen

Voorbeelden (Let op! Gebruik `MySqlClient` i.p.v. `SqlClient`!):

- boek hoofdstuk 25
- https://docs.microsoft.com/en-us/dotnet/framework/data/adonet/ado-net-code-examples
- http://csharp-station.com/Tutorial/AdoDotNet
- ...

1. Maak een nieuw Console-project en voeg https://www.nuget.org/packages/MySqlConnector/
toe. Probeer met de class `System.Data.MySqlClient.MySqlConnection` een werkende
verbinding te krijgen. Je zal een gepaste `ConnectionString` moeten opzoeken voor
MySql. Als de MySQL-server op een virtuele machine draait en je moet port forwarding
gebruiken, zou het kunnen dat je ook de TCP-poort in de `ConnectionString` moet toevoegen.

2. Probeer de 3 verschillende soorten queries uit met de 3 verschillende `Execute`-
methods van `MySqlCommand`

3. Naast connected toegang, waarbij er constant verbinding is met de database,
kan je ook gebruik maken van classes zoals `DataSet`, `DataTable` en `IDataAdapter`
die het mogelijk maken om met data te werken, zonder dat er verbinding is met de
database. Het is dan enkel de bedoeling om de data af en toe te **down- of uploaden**.

# Extra

Zie ook:

- https://nl.wikipedia.org/wiki/ADO.NET
- ...



