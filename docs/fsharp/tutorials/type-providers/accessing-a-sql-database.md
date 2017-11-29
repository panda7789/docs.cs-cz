---
title: "Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů (F#)"
description: "Další informace o použití (technologie LINQ to SQL) sqldataconnection – poskytovatel typů v F # 3.0 k vygenerování typy pro databázi SQL. Pokud máte připojení k databázi za provozu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1c413eb0-16a5-4c1a-9a4e-ad6877e645d6
ms.openlocfilehash: c99afc1121b4f0d6d05ef82681a32437ede06e42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a>Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů

> [!NOTE]
Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.  V tématu [FSharp.Data](http://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.

> [!NOTE]
Rozhraní API referenčních odkazů se dostanete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Tento návod popisuje, jak používat typ zprostředkovatele služby sqldataconnection – (technologie LINQ to SQL), který je k dispozici v F # 3.0 k vygenerování typy dat v databázi SQL, pokud máte aktivní připojení k databázi. Pokud nemáte aktivní připojení k databázi, ale nutné LINQ soubor schématu SQL (souboru DBML), najdete v části [návod: generování typů F # ze souboru DBML](generating-fsharp-types-from-dbml.md).

Tento návod ukazuje následující úlohy. V tomto pořadí návod proběhla úspěšně, musí být provedeny tyto úlohy:


- Příprava databáze testu

- Vytvoření projektu

- Nastavení zprostředkovatele typů

- Dotazování na data

- Práce s možnou hodnotou Null pole

- Volání uložené procedury

- Aktualizace databáze

- Provádění kódu jazyka Transact-SQL

- Pomocí kontextu úplné dat

- Odstraňování dat

- Vytvoření databáze testu (podle potřeby)

## <a name="preparing-a-test-database"></a>Příprava databáze testu
Na serveru, který je spuštěn SQL Server vytvořte databázi pro účely testování. Databázi můžete vytvořit skript v dolní části této stránky v části [vytvoření testovací databáze](#creating-a-test-database) k tomu.


#### <a name="to-prepare-a-test-database"></a>Příprava databáze testu

Chcete-li spustit skript vytvoření databáze, otevřete **zobrazení** nabídce a potom vyberte **Průzkumník objektů systému SQL Server** nebo zvolte Ctrl +\, klávesy Ctrl + S. V **Průzkumník objektů systému SQL Server** okně otevřete místní nabídku pro příslušnou instanci, zvolte **nový dotaz**, zkopírujte skript v dolní části této stránky a potom vložte skript do editoru. Pokud chcete spustit skript SQL, zvolte ikonu panelu nástrojů trojúhelníkovou symbolem, nebo zvolte klávesy Ctrl + Q. Další informace o **Průzkumník objektů systému SQL Server**, najdete v části [vývoj připojených databází](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).


## <a name="creating-the-project"></a>Vytvoření projektu
Dále vytvoříte projekt aplikace F #.


#### <a name="to-create-and-set-up-the-project"></a>Vytvoření a nastavení projektu

1. Vytvořte nový projekt aplikace F #.

2. Přidejte odkazy na [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), a také `System.Data`, a `System.Data.Linq`.

3. Otevřete obory přidáním následující řádky kódu do horní části kódu F # souboru Program.fs.

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. Stejně jako u většiny F # programů, může spustit kód v tomto názorném postupu jako kompilované programu, nebo ji můžete spustit interaktivně jako skript. Pokud byste radši chtěli použít skripty, otevřete místní nabídce uzlu projektu, vyberte **přidat novou položku**, přidání souboru skriptu F # a přidejte do skriptu kód v jednotlivých kroků. Je potřeba přidat následující řádky v horní části souboru k načtení odkazů na sestavení.

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  Každý blok kódu pak můžete vybrat, jak ho přidat a stiskněte klávesu Alt + Enter a spustíte ho v F # interaktivní.

## <a name="setting-up-a-type-provider"></a>Nastavení zprostředkovatele typů
V tomto kroku vytvoříte zprostředkovatele typů pro svého schématu databáze.


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a>Nastavit typ poskytovatele z databáze přímé připojení

Existují dvě důležité řádky kódu, které potřebujete k vytvoření typy, které můžete použít k dotazu na SQL databázi pomocí typ poskytovatele. Nejprve vytvořit instanci zprostředkovatele typu. K tomu, vytvořit, jak vypadá typ zkratka pro `SqlDataConnection` s statické obecný parametr. `SqlDataConnection`je typ zprostředkovatele SQL a neměla by být zaměňovat s `SqlConnection` typ, který je použit při programování pro technologii ADO.NET. Pokud máte databázi, která chcete připojit a mít připojovací řetězec, použijte následující kód k vyvolání typ poskytovatele. Nahraďte vlastní připojovací řetězec pro zadaný řetězec příklad. Například pokud jako by se tento server je MYSERVER a instanci databáze je INSTANCE, název databáze je databáze a chcete použít ověřování systému Windows pro přístup k databázi a pak připojovací řetězec zadaný v následujícím příkladu kódu.

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

Nyní máte typu, `dbSchema`, což je nadřazený typ, který obsahuje všechny vygenerované typy, které představují tabulky databáze. Objekt, máte také `db`, který obsahuje jako členy všechny tabulky v databázi. Názvy tabulek jsou vlastnosti a typ tyto vlastnosti je generován kompilátor jazyka F #. Typy sami zobrazí jako vnořené typy pod `dbSchema.ServiceTypes`. Žádná data načíst pro řádky tyto tabulky je proto instance příslušného typu, který byl vytvořen pro tuto tabulku. Název typu je `ServiceTypes.Table1`.

Seznamte se s Interpretace jazyka F #: dotazy na dotazy SQL, podívejte se na řádek, který nastaví `Log` vlastnost pro daný kontext data.

Chcete-li prozkoumat další typy vytvořené typ zprostředkovatele, přidejte následující kód.

```fsharp
let table1 = db.Table1
```

Pozastavte ukazatel myši nad `table1` zobrazíte jeho typu. Je její typ `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` a obecné argument vyplývá, že typ každý řádek je typ generovaného `dbSchema.ServiceTypes.Table1`. Kompilátor vytvoří podobně jako typ pro každou tabulku v databázi.

## <a name="querying-the-data"></a>Dotazování na data
V tomto kroku můžete napsat dotaz pomocí F # – výrazy dotazů.


#### <a name="to-query-the-data"></a>Postup dotazování na data

1. Nyní můžete vytvořte dotaz pro tuto tabulku v databázi. Přidejte následující kód.

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  Vzhled aplikace word `query` označuje, že to je výrazu dotazu, typ výpočetní výraz, který generuje kolekce výsledky podobné typické databázového dotazu. Pokud je ukazatel myši nad dotazu, se zobrazí, že se jedná o instanci [LINQ.QueryBuilder – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), typ, který definuje výpočetní výraz dotazu. Pokud se ukazatel myši přesunete `query1`, zobrazí se, že se jedná o instanci `System.Linq.IQueryable`. Jak již název naznačuje, `System.Linq.IQueryable` představuje data, který může být dotazován, není výsledek dotazu. Dotaz podléhá opožděné vyhodnocení, což znamená, že databáze je pouze dotaz-li dotaz. Poslední řádek předává dotaz prostřednictvím `Seq.iter`. Dotazy jsou vyčíslitelná a může být vstupní jako pořadí. Další informace najdete v tématu [výrazy dotazů](../../language-reference/query-expressions.md).

2. Nyní chcete do dotazu přidáte operátor dotazu. Existuje několik operátorů dotazu k dispozici, že můžete vytvořit složitější dotazy. Tento příklad také ukazuje, že můžete eliminovat proměnnou dotazu a místo toho použijte operátor kanálu.

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. Přidejte komplexnější dotaz s spojení dvou tabulek.

  ```fsharp
   query {
     for row1 in db.Table1 do
     join row2 in db.Table2 on (row1.Id = row2.Id)
     select (row1, row2)
   } |> Seq.iteri (fun index (row1, row2) ->
                   if (index = 0) then printfn "Table1.Id TestData1 TestData2 Name Table2.Id TestData1 TestData2 Name"
                   printfn "%d %d %f %s %d %d %f %s" row1.Id row1.TestData1 row1.TestData2 row1.Name
                     row2.Id (row2.TestData1.GetValueOrDefault()) (row2.TestData2.GetValueOrDefault()) row2.Name)
```

4. V kódu reálného parametry v dotazu jsou obvykle hodnoty nebo proměnné, není kompilaci konstanty. Přidejte následující kód, který zabalí dotazu ve funkci, která přebírá parametr a potom volá tuto funkci s hodnotou 10.

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a>Práce s možnou hodnotou Null pole
V databázích pole často povolit hodnoty null. V systému typ rozhraní .NET nemůžete použít obyčejnou číselné datové typy pro data, která umožňuje hodnoty Null protože nemají tyto typy jako možná hodnota null. Proto tyto hodnoty jsou reprezentované pomocí instance `System.Nullable` typu. Ne přístup hodnotu z těchto polí přímo s název pole, je nutné přidat některými dalšími kroky. Můžete použít `System.Nullable.Value` vlastnost, která má přístup k hodnotě základní typ s možnou hodnotou Null. `System.Nullable.Value` Vlastnost vyvolá výjimku, pokud se objekt místo s hodnotou null. Můžete použít `System.Nullable.HasValue` Boolean metoda určí, zda existuje hodnota, nebo použijte `System.Nullable.GetValueOrDefault()` zajistit, že máte ve všech případech skutečnou hodnotu. Pokud používáte `System.Nullable.GetValueOrDefault()` a v databázi je null, pak je nahrazen hodnotou například prázdný řetězec pro typy řetězců, 0 pro integrální typy nebo 0,0 pro plovoucí bodu typy.

Když potřebujete provést testy rovnosti nebo porovnání s možnou hodnotou Null v `where` klauzuli v dotazu, můžete použít s možnou hodnotou Null operátory v nalezen [LINQ.nullableoperators – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d). Toto jsou jako regulární relační operátory `=`, `>`, `<=`a tak dále, s tím rozdílem, že otazník se zobrazí vlevo nebo vpravo od operátor kde jsou hodnoty Null. Například operátor `>?` je více – než – operátor s hodnotou Null na pravé straně. Způsob práce těchto operátorů je, že pokud stranách výrazu hodnotu null, je vyhodnocen `false`. V `where` klauzule to obvykle znamená, že řádky, které obsahují pole s hodnotou null se není vybrána a nebyla vrácena ve výsledcích dotazu.


#### <a name="to-work-with-nullable-fields"></a>Pro práci s pole s možnou hodnotou Null

Následující kód ukazuje práce s hodnotami Null. předpokládáme, že **TestData1** je na celé číslo pole, která umožňuje hodnoty Null.

```fsharp
query {
  for row in db.Table2 do
  where (row.TestData1.HasValue && row.TestData1.Value > 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
  for row in db.Table2 do
  // Use a nullable operator ?>
  where (row.TestData1 ?> 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="calling-a-stored-procedure"></a>Volání uložené procedury
Všechny uložené procedury v databázi lze volat z F #. Musíte nastavit statický parametr `StoredProcedures` k `true` v instance typu zprostředkovatele. Typ zprostředkovatele `SqlDataConnection` obsahuje několik statických metod, které můžete použít ke konfiguraci typy, které se generují. Úplný popis těchto, najdete v části [sqldataconnection – zprostředkovatel typu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d). Metoda na datový typ kontextu se generuje pro každou uložené procedury.


#### <a name="to-call-a-stored-procedure"></a>Postup volání uložené procedury

Pokud uložené procedury přijímá parametry, které jsou s možnou hodnotou Null, je třeba předat odpovídající `System.Nullable` hodnotu. Návratová hodnota metody uložené procedury, která vrací skalární hodnota nebo tabulku je `System.Data.Linq.ISingleResult`, která obsahuje vlastnosti, které vám umožní přístup k vrácená data. Argument typu pro `System.Data.Linq.ISingleResult` závisí na konkrétní postup a je také jeden z typů, které generuje typ poskytovatele. Pro uloženou proceduru s názvem `Procedure1`, typ je `Procedure1Result`. Typ `Procedure1Result` obsahuje názvy sloupců v tabulce vrácené, nebo pro uložené procedury, jež vrací skalární hodnotu reprezentuje návratovou hodnotu.

Následující kód předpokládá, že je procedura `Procedure1` v databázi, která přijímá jako parametry dvě s možnou hodnotou Null celá čísla, spouští dotaz, který vrátí sloupec s názvem `TestData1`a vrátí celé číslo.

```fsharp
type schema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;", StoredProcedures = true>

let testdb = schema.GetDataContext()

let nullable value = new System.Nullable<_>(value)

let callProcedure1 a b =
  let results = testdb.Procedure1(nullable a, nullable b)
  for result in results do
    printfn "%d" (result.TestData1.GetValueOrDefault())
  results.ReturnValue :?> int

printfn "Return Value: %d" (callProcedure1 10 20)
```

## <a name="updating-the-database"></a>Aktualizace databáze
Typ LINQ DataContext obsahuje metody, které usnadňují provádět aktualizace databáze zpracovaných plně typové způsobem s generovaného typy.


#### <a name="to-update-the-database"></a>Postup aktualizace databáze

1. V následujícím kódu několik řádků se přidají do databáze. Pokud přidáváte jenom řádek, můžete použít `System.Data.Linq.Table.InsertOnSubmit()` k určení nového řádku přidat. Při vkládání více řádků, je měli vložíte do kolekce a volání `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`. Při volání jedné z těchto metod, databáze není změnit okamžitě. Je třeba volat `System.Data.Linq.DataContext.SubmitChanges` skutečně provést změny. Ve výchozím nastavení, vše, co můžete udělat předtím, než volání `System.Data.Linq.DataContext.SubmitChanges` je implicitně součástí stejné transakci.

 ```fsharp
   let newRecord = new dbSchema.ServiceTypes.Table1(Id = 100,
                                                    TestData1 = 35, 
                                                    TestData2 = 2.0,
                                                    Name = "Testing123")

   let newValues =
     [ for i in [1 .. 10] ->
       new dbSchema.ServiceTypes.Table3(Id = 700 + i,
         Name = "Testing" + i.ToString(),
         Data = i) ]

   // Insert the new data into the database.
   db.Table1.InsertOnSubmit(newRecord)
   db.Table3.InsertAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully inserted new rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

2. Nyní vyčistěte řádky voláním operace odstranění.

  ```fsharp
   // Now delete what was added.
   db.Table1.DeleteOnSubmit(newRecord)
   db.Table3.DeleteAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully deleted all pending rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="executing-transact-sql-code"></a>Provádění kódu jazyka Transact-SQL
Transact-SQL můžete zadat také přímo pomocí `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` metodu `DataContext` třídy.


#### <a name="to-execute-custom-sql-commands"></a>K provedení vlastní příkazy SQL

Následující kód ukazuje, jak má odeslat příkazy SQL k vložení záznamu do tabulky a také k odstranění záznamu z tabulky.

```fsharp
try
  db.DataContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'Testing', 55)") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message

try //AND Name = 'Testing' AND Data = 55
  db.DataContext.ExecuteCommand("DELETE FROM Table3 WHERE Id = 102 ") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="using-the-full-data-context"></a>Pomocí kontextu úplné dat
V předchozích příkladech `GetDataContext` metoda byla použita k získání, co se nazývá *kontextu zjednodušené dat* pro schéma databáze. Kontext zjednodušené dat je snazší použijte, pokud jsou tvorbu dotazů, protože nejsou k dispozici jako mnoho členů. Proto při procházení vlastností v technologii IntelliSense, můžete se zaměřit na strukturu databáze, jako jsou tabulky a uložené procedury. Je však omezení co můžete dělat s kontextem zjednodušené data. Úplná data kontextu, který poskytuje schopnost provádět další akce. je také k dispozici je umístěný v `ServiceTypes` a má název *DataContext* statické parametr, pokud jste zadali ho. Pokud není zadán ho, název typu kontextu dat vygeneruje pro vás SqlMetal.exe podle jiného vstupu. Úplná data kontextu dědí z `System.Data.Linq.DataContext` a zveřejňuje členy její základní třída, včetně odkazů na typy dat ADO.NET, jako `Connection` objektu, metody, jako `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` a `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` používané pro zápis dotazů v SQL, a také znamená pro práci s transakce explicitně.


#### <a name="to-use-the-full-data-context"></a>Použití kontextu úplné dat

Následující kód ukazuje získání úplné datový objekt kontextu a pomocí příkazy přímo s databází. V takovém případě jsou dva příkazy provádět v rámci stejné transakci.

```fsharp
let dbConnection = testdb.Connection
let fullContext = new dbSchema.ServiceTypes.MyDatabase(dbConnection)

dbConnection.Open()

let transaction = dbConnection.BeginTransaction()
fullContext.Transaction <- transaction

try
  let result1 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'A', 55)")
  printfn "ExecuteCommand Result: %d" result1
  let result2 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (103, 'B', -2)")
  printfn "ExecuteCommand Result: %d" result2
  if (result1 <> 1 || result2 <> 1) then
    transaction.Rollback()
    printfn "Rolled back creation of two new rows."
  else
    transaction.Commit()
  printfn "Successfully committed two new rows."
with
| exn ->
  transaction.Rollback()
  printfn "Rolled back creation of two new rows due to exception:\n%s" exn.Message

dbConnection.Close()
```

## <a name="deleting-data"></a>Odstraňování dat
Tento krok popisuje postup odstranění řádků z tabulky data.


#### <a name="to-delete-rows-from-the-database"></a>Odstranění řádků z databáze

Nyní, vyčištění žádné přidány řádky napsáním funkci, která odstraní řádky ze zadané tabulky, instanci `System.Data.Linq.Table` třídy. Pak zápis dotaz, který najde všechny řádky, které chcete odstranit a zřetězit výsledků dotazu do `deleteRows` funkce. Tento kód využívá schopnost poskytovat částečné aplikace argumenty funkce.

```fsharp
let deleteRowsFrom (table:Table<_>) rows =
  table.DeleteAllOnSubmit(rows)

query {
  for rows in db.Table3 do
  where (rows.Id > 10)
  select rows
} |> deleteRowsFrom db.Table3

db.DataContext.SubmitChanges()
printfn "Successfully deleted rows with Id greater than 10 in Table3."
```

## <a name="creating-a-test-database"></a>Vytvoření databáze testu
V této části se dozvíte, jak nastavit testovací databáze pro použití v tomto návodu.

Všimněte si, že pokud změníte databázi nějakým způsobem, budete muset resetovat zprostředkovatel typu. Pokud chcete resetovat typ zprostředkovatele, znovu sestavit nebo vyčistit projekt, který obsahuje tohoto zprostředkovatele zadejte.


#### <a name="to-create-the-test-database"></a>Chcete-li vytvořit testovací databáze

1. V **Průzkumníka serveru**, otevřete místní nabídku pro **připojení dat** uzel a zvolte **přidat připojení**. **Přidat připojení** zobrazí se dialogové okno.

2. V **název serveru** pole, zadejte název instance systému SQL Server, ke které máte přístup pro správu nebo pokud nemáte přístup k serveru, zadejte (localdb\v11.0). SQL Express LocalDB poskytuje odlehčený databázový server pro vývoj a testování v počítači. Vytvoří se nový uzel v **Průzkumníka serveru** pod **datová připojení**. Další informace o LocalDB najdete v tématu [návod: Vytvoření místního souboru databáze v sadě Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).

3. Otevřete místní nabídku pro nový uzel připojení a vyberte **nový dotaz**.

4. Zkopírujte následující skript SQL, vložte jej do editoru dotazů a potom zvolte **Execute** tlačítka na panelu nástrojů nebo zvolte klávesy Ctrl + Shift + E.

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
  DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase;
GO

-- Specify a simple recovery model 
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase 
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

-- Create the Table1 table.
CREATE TABLE [dbo].[Table1] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NOT NULL,
  [TestData2] FLOAT (53) NOT NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);

-- Create the Table2 table.
CREATE TABLE [dbo].[Table2] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NULL,
  [TestData2] FLOAT (53) NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);


-- Create the Table3 table.
CREATE TABLE [dbo].[Table3] (
  [Id]   INT           NOT NULL,
  [Name] NVARCHAR (50) NOT NULL,
  [Data] INT           NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
  );
GO

CREATE PROCEDURE [dbo].[Procedure1]
  @param1 int = 0,
  @param2 int
AS
SELECT TestData1 FROM Table1
RETURN 0
GO

USE MyDatabase

-- Insert data into the Table1 table.
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');

-- Insert data into the Table2 table.
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(3, NULL, NULL, 'Testing3');

-- Insert data into the Table3 table.
INSERT INTO Table3 (Id, Name, Data)
  VALUES (1, 'Testing1', 10);
INSERT INTO Table3 (Id, Name, Data)
  VALUES (2, 'Testing2', 100);
```


## <a name="see-also"></a>Viz také
[Zprostředkovatelé typů](index.md)

[Sqldataconnection – zprostředkovatel typu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[Návod: Generování typů F # ze souboru DBML](generating-fsharp-types-from-dbml.md)

[Výrazy dotazů](../../language-reference/query-expressions.md)

[Technologie LINQ to SQL](https://msdn.microsoft.com/library/bb386976)

[SqlMetal.exe & #40; Nástroj pro vytváření kódu & #41;](https://msdn.microsoft.com/library/bb386987)
