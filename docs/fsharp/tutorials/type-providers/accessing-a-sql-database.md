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
ms.openlocfilehash: 7177eca33ded712308bbc6198040d833b7364d55
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a><span data-ttu-id="f283b-104">Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="f283b-104">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="f283b-105">Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="f283b-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="f283b-106">V tématu [FSharp.Data](http://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="f283b-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="f283b-107">Rozhraní API referenčních odkazů se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="f283b-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="f283b-108">Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="f283b-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="f283b-109">Tento návod popisuje, jak používat typ zprostředkovatele služby sqldataconnection – (technologie LINQ to SQL), který je k dispozici v F # 3.0 k vygenerování typy dat v databázi SQL, pokud máte aktivní připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="f283b-109">This walkthrough explains how to use the SqlDataConnection (LINQ to SQL) type provider that is available in F# 3.0 to generate types for data in a SQL database when you have a live connection to a database.</span></span> <span data-ttu-id="f283b-110">Pokud nemáte aktivní připojení k databázi, ale nutné LINQ soubor schématu SQL (souboru DBML), najdete v části [návod: generování typů F # ze souboru DBML](generating-fsharp-types-from-dbml.md).</span><span class="sxs-lookup"><span data-stu-id="f283b-110">If you do not have a live connection to a database, but you do have a LINQ to SQL schema file (DBML file), see [Walkthrough: Generating F# Types from a DBML File](generating-fsharp-types-from-dbml.md).</span></span>

<span data-ttu-id="f283b-111">Tento návod ukazuje následující úlohy.</span><span class="sxs-lookup"><span data-stu-id="f283b-111">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="f283b-112">V tomto pořadí návod proběhla úspěšně, musí být provedeny tyto úlohy:</span><span class="sxs-lookup"><span data-stu-id="f283b-112">These tasks must be performed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="f283b-113">Příprava databáze testu</span><span class="sxs-lookup"><span data-stu-id="f283b-113">Preparing a test database</span></span>

- <span data-ttu-id="f283b-114">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="f283b-114">Creating the project</span></span>

- <span data-ttu-id="f283b-115">Nastavení zprostředkovatele typů</span><span class="sxs-lookup"><span data-stu-id="f283b-115">Setting up a type provider</span></span>

- <span data-ttu-id="f283b-116">Dotazování na data</span><span class="sxs-lookup"><span data-stu-id="f283b-116">Querying the data</span></span>

- <span data-ttu-id="f283b-117">Práce s možnou hodnotou Null pole</span><span class="sxs-lookup"><span data-stu-id="f283b-117">Working with nullable fields</span></span>

- <span data-ttu-id="f283b-118">Volání uložené procedury</span><span class="sxs-lookup"><span data-stu-id="f283b-118">Calling a stored procedure</span></span>

- <span data-ttu-id="f283b-119">Aktualizace databáze</span><span class="sxs-lookup"><span data-stu-id="f283b-119">Updating the database</span></span>

- <span data-ttu-id="f283b-120">Provádění kódu jazyka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f283b-120">Executing Transact-SQL code</span></span>

- <span data-ttu-id="f283b-121">Pomocí kontextu úplné dat</span><span class="sxs-lookup"><span data-stu-id="f283b-121">Using the full data context</span></span>

- <span data-ttu-id="f283b-122">Odstraňování dat</span><span class="sxs-lookup"><span data-stu-id="f283b-122">Deleting data</span></span>

- <span data-ttu-id="f283b-123">Vytvoření databáze testu (podle potřeby)</span><span class="sxs-lookup"><span data-stu-id="f283b-123">Create a test database (as needed)</span></span>

## <a name="preparing-a-test-database"></a><span data-ttu-id="f283b-124">Příprava databáze testu</span><span class="sxs-lookup"><span data-stu-id="f283b-124">Preparing a Test Database</span></span>
<span data-ttu-id="f283b-125">Na serveru, který je spuštěn SQL Server vytvořte databázi pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="f283b-125">On a server that's running SQL Server, create a database for testing purposes.</span></span> <span data-ttu-id="f283b-126">Databázi můžete vytvořit skript v dolní části této stránky v části [vytvoření testovací databáze](#creating-a-test-database) k tomu.</span><span class="sxs-lookup"><span data-stu-id="f283b-126">You can use the database create script at the bottom of this page in the section [Creating a test database](#creating-a-test-database) to do this.</span></span>


#### <a name="to-prepare-a-test-database"></a><span data-ttu-id="f283b-127">Příprava databáze testu</span><span class="sxs-lookup"><span data-stu-id="f283b-127">To prepare a test database</span></span>

<span data-ttu-id="f283b-128">Chcete-li spustit skript vytvoření databáze, otevřete **zobrazení** nabídce a potom vyberte **Průzkumník objektů systému SQL Server** nebo zvolte Ctrl +\, klávesy Ctrl + S.</span><span class="sxs-lookup"><span data-stu-id="f283b-128">To run the MyDatabase Create Script, open the **View** menu, and then choose **SQL Server Object Explorer** or choose the Ctrl+\, Ctrl+S keys.</span></span> <span data-ttu-id="f283b-129">V **Průzkumník objektů systému SQL Server** okně otevřete místní nabídku pro příslušnou instanci, zvolte **nový dotaz**, zkopírujte skript v dolní části této stránky a potom vložte skript do editoru.</span><span class="sxs-lookup"><span data-stu-id="f283b-129">In **SQL Server Object Explorer** window, open the shortcut menu for the appropriate instance, choose **New Query**, copy the script at the bottom of this page, and then paste the script into the editor.</span></span> <span data-ttu-id="f283b-130">Pokud chcete spustit skript SQL, zvolte ikonu panelu nástrojů trojúhelníkovou symbolem, nebo zvolte klávesy Ctrl + Q.</span><span class="sxs-lookup"><span data-stu-id="f283b-130">To run the SQL script, choose the toolbar icon with the triangular symbol, or choose the Ctrl+Q keys.</span></span> <span data-ttu-id="f283b-131">Další informace o **Průzkumník objektů systému SQL Server**, najdete v části [vývoj připojených databází](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span><span class="sxs-lookup"><span data-stu-id="f283b-131">For more information about **SQL Server Object Explorer**, see [Connected Database Development](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span></span>


## <a name="creating-the-project"></a><span data-ttu-id="f283b-132">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="f283b-132">Creating the project</span></span>
<span data-ttu-id="f283b-133">Dále vytvoříte projekt aplikace F #.</span><span class="sxs-lookup"><span data-stu-id="f283b-133">Next, you create an F# application project.</span></span>


#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="f283b-134">Vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="f283b-134">To create and set up the project</span></span>

1. <span data-ttu-id="f283b-135">Vytvořte nový projekt aplikace F #.</span><span class="sxs-lookup"><span data-stu-id="f283b-135">Create a new F# Application project.</span></span>

2. <span data-ttu-id="f283b-136">Přidejte odkazy na [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), a také `System.Data`, a `System.Data.Linq`.</span><span class="sxs-lookup"><span data-stu-id="f283b-136">Add references to [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), as well as `System.Data`, and `System.Data.Linq`.</span></span>

3. <span data-ttu-id="f283b-137">Otevřete obory přidáním následující řádky kódu do horní části kódu F # souboru Program.fs.</span><span class="sxs-lookup"><span data-stu-id="f283b-137">Open the appropriate namespaces by adding the following lines of code to the top of your F# code file Program.fs.</span></span>

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. <span data-ttu-id="f283b-138">Stejně jako u většiny F # programů, může spustit kód v tomto názorném postupu jako kompilované programu, nebo ji můžete spustit interaktivně jako skript.</span><span class="sxs-lookup"><span data-stu-id="f283b-138">As with most F# programs, you can execute the code in this walkthrough as a compiled program, or you can run it interactively as a script.</span></span> <span data-ttu-id="f283b-139">Pokud byste radši chtěli použít skripty, otevřete místní nabídce uzlu projektu, vyberte **přidat novou položku**, přidání souboru skriptu F # a přidejte do skriptu kód v jednotlivých kroků.</span><span class="sxs-lookup"><span data-stu-id="f283b-139">If you prefer to use scripts, open the shortcut menu for the project node, select **Add New Item**, add an F# script file, and add the code in each step to the script.</span></span> <span data-ttu-id="f283b-140">Je potřeba přidat následující řádky v horní části souboru k načtení odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="f283b-140">You will need to add the following lines at the top of the file to load the assembly references.</span></span>

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  <span data-ttu-id="f283b-141">Každý blok kódu pak můžete vybrat, jak ho přidat a stiskněte klávesu Alt + Enter a spustíte ho v F # interaktivní.</span><span class="sxs-lookup"><span data-stu-id="f283b-141">You can then select each block of code as you add it and press Alt+Enter to run it in F# Interactive.</span></span>

## <a name="setting-up-a-type-provider"></a><span data-ttu-id="f283b-142">Nastavení zprostředkovatele typů</span><span class="sxs-lookup"><span data-stu-id="f283b-142">Setting up a type provider</span></span>
<span data-ttu-id="f283b-143">V tomto kroku vytvoříte zprostředkovatele typů pro svého schématu databáze.</span><span class="sxs-lookup"><span data-stu-id="f283b-143">In this step, you create a type provider for your database schema.</span></span>


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a><span data-ttu-id="f283b-144">Nastavit typ poskytovatele z databáze přímé připojení</span><span class="sxs-lookup"><span data-stu-id="f283b-144">To set up the type provider from a direct database connection</span></span>

<span data-ttu-id="f283b-145">Existují dvě důležité řádky kódu, které potřebujete k vytvoření typy, které můžete použít k dotazu na SQL databázi pomocí typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="f283b-145">There are two critical lines of code that you need in order to create the types that you can use to query a SQL database using the type provider.</span></span> <span data-ttu-id="f283b-146">Nejprve vytvořit instanci zprostředkovatele typu.</span><span class="sxs-lookup"><span data-stu-id="f283b-146">First, you instantiate the type provider.</span></span> <span data-ttu-id="f283b-147">K tomu, vytvořit, jak vypadá typ zkratka pro `SqlDataConnection` s statické obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="f283b-147">To do this, create what looks like a type abbreviation for a `SqlDataConnection` with a static generic parameter.</span></span> <span data-ttu-id="f283b-148">`SqlDataConnection`je typ zprostředkovatele SQL a neměla by být zaměňovat s `SqlConnection` typ, který je použit při programování pro technologii ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f283b-148">`SqlDataConnection` is a SQL type provider, and should not be confused with `SqlConnection` type that is used in ADO.NET programming.</span></span> <span data-ttu-id="f283b-149">Pokud máte databázi, která chcete připojit a mít připojovací řetězec, použijte následující kód k vyvolání typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="f283b-149">If you have a database that you want to connect to, and have a connection string, use the following code to invoke the type provider.</span></span> <span data-ttu-id="f283b-150">Nahraďte vlastní připojovací řetězec pro zadaný řetězec příklad.</span><span class="sxs-lookup"><span data-stu-id="f283b-150">Substitute your own connection string for the example string given.</span></span> <span data-ttu-id="f283b-151">Například pokud jako by se tento server je MYSERVER a instanci databáze je INSTANCE, název databáze je databáze a chcete použít ověřování systému Windows pro přístup k databázi a pak připojovací řetězec zadaný v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f283b-151">For example, if your server is MYSERVER and the database instance is INSTANCE, the database name is MyDatabase, and you want to use Windows Authentication to access the database, then the connection string would be as given in the following example code.</span></span>

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

<span data-ttu-id="f283b-152">Nyní máte typu, `dbSchema`, což je nadřazený typ, který obsahuje všechny vygenerované typy, které představují tabulky databáze.</span><span class="sxs-lookup"><span data-stu-id="f283b-152">Now you have a type, `dbSchema`, which is a parent type that contains all the generated types that represent database tables.</span></span> <span data-ttu-id="f283b-153">Objekt, máte také `db`, který obsahuje jako členy všechny tabulky v databázi.</span><span class="sxs-lookup"><span data-stu-id="f283b-153">You also have an object, `db`, which has as its members all the tables in the database.</span></span> <span data-ttu-id="f283b-154">Názvy tabulek jsou vlastnosti a typ tyto vlastnosti je generován kompilátor jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="f283b-154">The table names are properties, and the type of these properties is generated by the F# compiler.</span></span> <span data-ttu-id="f283b-155">Typy sami zobrazí jako vnořené typy pod `dbSchema.ServiceTypes`.</span><span class="sxs-lookup"><span data-stu-id="f283b-155">The types themselves appear as nested types under `dbSchema.ServiceTypes`.</span></span> <span data-ttu-id="f283b-156">Žádná data načíst pro řádky tyto tabulky je proto instance příslušného typu, který byl vytvořen pro tuto tabulku.</span><span class="sxs-lookup"><span data-stu-id="f283b-156">Therefore, any data retrieved for rows of these tables is an instance of the appropriate type that was generated for that table.</span></span> <span data-ttu-id="f283b-157">Název typu je `ServiceTypes.Table1`.</span><span class="sxs-lookup"><span data-stu-id="f283b-157">The name of the type is `ServiceTypes.Table1`.</span></span>

<span data-ttu-id="f283b-158">Seznamte se s Interpretace jazyka F #: dotazy na dotazy SQL, podívejte se na řádek, který nastaví `Log` vlastnost pro daný kontext data.</span><span class="sxs-lookup"><span data-stu-id="f283b-158">To familiarize yourself with how the F# language interprets queries into SQL queries, review the line that sets the `Log` property on the data context.</span></span>

<span data-ttu-id="f283b-159">Chcete-li prozkoumat další typy vytvořené typ zprostředkovatele, přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="f283b-159">To further explore the types created by the type provider, add the following code.</span></span>

```fsharp
let table1 = db.Table1
```

<span data-ttu-id="f283b-160">Pozastavte ukazatel myši nad `table1` zobrazíte jeho typu.</span><span class="sxs-lookup"><span data-stu-id="f283b-160">Hover over `table1` to see its type.</span></span> <span data-ttu-id="f283b-161">Je její typ `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` a obecné argument vyplývá, že typ každý řádek je typ generovaného `dbSchema.ServiceTypes.Table1`.</span><span class="sxs-lookup"><span data-stu-id="f283b-161">Its type is `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` and the generic argument implies that the type of each row is the generated type, `dbSchema.ServiceTypes.Table1`.</span></span> <span data-ttu-id="f283b-162">Kompilátor vytvoří podobně jako typ pro každou tabulku v databázi.</span><span class="sxs-lookup"><span data-stu-id="f283b-162">The compiler creates a similar type for each table in the database.</span></span>

## <a name="querying-the-data"></a><span data-ttu-id="f283b-163">Dotazování na data</span><span class="sxs-lookup"><span data-stu-id="f283b-163">Querying the data</span></span>
<span data-ttu-id="f283b-164">V tomto kroku můžete napsat dotaz pomocí F # – výrazy dotazů.</span><span class="sxs-lookup"><span data-stu-id="f283b-164">In this step, you write a query using F# query expressions.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="f283b-165">Postup dotazování na data</span><span class="sxs-lookup"><span data-stu-id="f283b-165">To query the data</span></span>

1. <span data-ttu-id="f283b-166">Nyní můžete vytvořte dotaz pro tuto tabulku v databázi.</span><span class="sxs-lookup"><span data-stu-id="f283b-166">Now create a query for that table in the database.</span></span> <span data-ttu-id="f283b-167">Přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="f283b-167">Add the following code.</span></span>

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  <span data-ttu-id="f283b-168">Vzhled aplikace word `query` označuje, že to je výrazu dotazu, typ výpočetní výraz, který generuje kolekce výsledky podobné typické databázového dotazu.</span><span class="sxs-lookup"><span data-stu-id="f283b-168">The appearance of the word `query` indicates that this is a query expression, a type of computation expression that generates a collection of results similar of a typical database query.</span></span> <span data-ttu-id="f283b-169">Pokud je ukazatel myši nad dotazu, se zobrazí, že se jedná o instanci [LINQ.QueryBuilder – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), typ, který definuje výpočetní výraz dotazu.</span><span class="sxs-lookup"><span data-stu-id="f283b-169">If you hover over query, you will see that it is an instance of [Linq.QueryBuilder Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), a type that defines the query computation expression.</span></span> <span data-ttu-id="f283b-170">Pokud se ukazatel myši přesunete `query1`, zobrazí se, že se jedná o instanci `System.Linq.IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="f283b-170">If you hover over `query1`, you will see that it is an instance of `System.Linq.IQueryable`.</span></span> <span data-ttu-id="f283b-171">Jak již název naznačuje, `System.Linq.IQueryable` představuje data, který může být dotazován, není výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="f283b-171">As the name suggests, `System.Linq.IQueryable` represents data that may be queried, not the result of a query.</span></span> <span data-ttu-id="f283b-172">Dotaz podléhá opožděné vyhodnocení, což znamená, že databáze je pouze dotaz-li dotaz.</span><span class="sxs-lookup"><span data-stu-id="f283b-172">A query is subject to lazy evaluation, which means that the database is only queried when the query is evaluated.</span></span> <span data-ttu-id="f283b-173">Poslední řádek předává dotaz prostřednictvím `Seq.iter`.</span><span class="sxs-lookup"><span data-stu-id="f283b-173">The final line passes the query through `Seq.iter`.</span></span> <span data-ttu-id="f283b-174">Dotazy jsou vyčíslitelná a může být vstupní jako pořadí.</span><span class="sxs-lookup"><span data-stu-id="f283b-174">Queries are enumerable and may be iterated like sequences.</span></span> <span data-ttu-id="f283b-175">Další informace najdete v tématu [výrazy dotazů](../../language-reference/query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f283b-175">For more information, see [Query Expressions](../../language-reference/query-expressions.md).</span></span>

2. <span data-ttu-id="f283b-176">Nyní chcete do dotazu přidáte operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="f283b-176">Now add a query operator to the query.</span></span> <span data-ttu-id="f283b-177">Existuje několik operátorů dotazu k dispozici, že můžete vytvořit složitější dotazy.</span><span class="sxs-lookup"><span data-stu-id="f283b-177">There are a number of query operators available that you can use to construct more complex queries.</span></span> <span data-ttu-id="f283b-178">Tento příklad také ukazuje, že můžete eliminovat proměnnou dotazu a místo toho použijte operátor kanálu.</span><span class="sxs-lookup"><span data-stu-id="f283b-178">This example also shows that you can eliminate the query variable and use a pipeline operator instead.</span></span>

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. <span data-ttu-id="f283b-179">Přidejte komplexnější dotaz s spojení dvou tabulek.</span><span class="sxs-lookup"><span data-stu-id="f283b-179">Add a more complex query with a join of two tables.</span></span>

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

4. <span data-ttu-id="f283b-180">V kódu reálného parametry v dotazu jsou obvykle hodnoty nebo proměnné, není kompilaci konstanty.</span><span class="sxs-lookup"><span data-stu-id="f283b-180">In real-world code, the parameters in your query are usually values or variables, not compile-time constants.</span></span> <span data-ttu-id="f283b-181">Přidejte následující kód, který zabalí dotazu ve funkci, která přebírá parametr a potom volá tuto funkci s hodnotou 10.</span><span class="sxs-lookup"><span data-stu-id="f283b-181">Add the following code that wraps a query in a function that takes a parameter, and then calls that function with the value 10.</span></span>

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a><span data-ttu-id="f283b-182">Práce s možnou hodnotou Null pole</span><span class="sxs-lookup"><span data-stu-id="f283b-182">Working with nullable fields</span></span>
<span data-ttu-id="f283b-183">V databázích pole často povolit hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="f283b-183">In databases, fields often allow null values.</span></span> <span data-ttu-id="f283b-184">V systému typ rozhraní .NET nemůžete použít obyčejnou číselné datové typy pro data, která umožňuje hodnoty Null protože nemají tyto typy jako možná hodnota null.</span><span class="sxs-lookup"><span data-stu-id="f283b-184">In the .NET type system, you cannot use the ordinary numerical data types for data that allows nulls because those types do not have null as a possible value.</span></span> <span data-ttu-id="f283b-185">Proto tyto hodnoty jsou reprezentované pomocí instance `System.Nullable` typu.</span><span class="sxs-lookup"><span data-stu-id="f283b-185">Therefore, these values are represented by instances of `System.Nullable` type.</span></span> <span data-ttu-id="f283b-186">Ne přístup hodnotu z těchto polí přímo s název pole, je nutné přidat některými dalšími kroky.</span><span class="sxs-lookup"><span data-stu-id="f283b-186">Instead of accessing the value of such fields directly with the name of the field, you need to add some extra steps.</span></span> <span data-ttu-id="f283b-187">Můžete použít `System.Nullable.Value` vlastnost, která má přístup k hodnotě základní typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="f283b-187">You can use the `System.Nullable.Value` property to access the underlying value of a nullable type.</span></span> <span data-ttu-id="f283b-188">`System.Nullable.Value` Vlastnost vyvolá výjimku, pokud se objekt místo s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="f283b-188">The `System.Nullable.Value` property throws an exception if the object is null rather than having a value.</span></span> <span data-ttu-id="f283b-189">Můžete použít `System.Nullable.HasValue` Boolean metoda určí, zda existuje hodnota, nebo použijte `System.Nullable.GetValueOrDefault()` zajistit, že máte ve všech případech skutečnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f283b-189">You can use the `System.Nullable.HasValue` Boolean method to determine if a value exists, or use `System.Nullable.GetValueOrDefault()` to ensure that you have an actual value in all cases.</span></span> <span data-ttu-id="f283b-190">Pokud používáte `System.Nullable.GetValueOrDefault()` a v databázi je null, pak je nahrazen hodnotou například prázdný řetězec pro typy řetězců, 0 pro integrální typy nebo 0,0 pro plovoucí bodu typy.</span><span class="sxs-lookup"><span data-stu-id="f283b-190">If you use `System.Nullable.GetValueOrDefault()` and there is a null in the database, then it is replaced with a value such as an empty string for string types, 0 for integral types or 0.0 for floating point types.</span></span>

<span data-ttu-id="f283b-191">Když potřebujete provést testy rovnosti nebo porovnání s možnou hodnotou Null v `where` klauzuli v dotazu, můžete použít s možnou hodnotou Null operátory v nalezen [LINQ.nullableoperators – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="f283b-191">When you need to perform equality tests or comparisons on nullable values in a `where` clause in a query, you can use the nullable operators found in the [Linq.NullableOperators Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span></span> <span data-ttu-id="f283b-192">Toto jsou jako regulární relační operátory `=`, `>`, `<=`a tak dále, s tím rozdílem, že otazník se zobrazí vlevo nebo vpravo od operátor kde jsou hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="f283b-192">These are like the regular comparison operators `=`, `>`, `<=`, and so on, except that a question mark appears on the left or right of the operator where the nullable values are.</span></span> <span data-ttu-id="f283b-193">Například operátor `>?` je více – než – operátor s hodnotou Null na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="f283b-193">For example, the operator `>?` is a greater-than operator with a nullable value on the right.</span></span> <span data-ttu-id="f283b-194">Způsob práce těchto operátorů je, že pokud stranách výrazu hodnotu null, je vyhodnocen `false`.</span><span class="sxs-lookup"><span data-stu-id="f283b-194">The way these operators work is that if either side of the expression is null, the expression evaluates to `false`.</span></span> <span data-ttu-id="f283b-195">V `where` klauzule to obvykle znamená, že řádky, které obsahují pole s hodnotou null se není vybrána a nebyla vrácena ve výsledcích dotazu.</span><span class="sxs-lookup"><span data-stu-id="f283b-195">In a `where` clause, this generally means that the rows that contain null fields are not selected and not returned in the query results.</span></span>


#### <a name="to-work-with-nullable-fields"></a><span data-ttu-id="f283b-196">Pro práci s pole s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="f283b-196">To work with nullable fields</span></span>

<span data-ttu-id="f283b-197">Následující kód ukazuje práce s hodnotami Null. předpokládáme, že **TestData1** je na celé číslo pole, která umožňuje hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="f283b-197">The following code shows working with nullable values; assume that **TestData1** is an integer field that allows nulls.</span></span>

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

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="f283b-198">Volání uložené procedury</span><span class="sxs-lookup"><span data-stu-id="f283b-198">Calling a stored procedure</span></span>
<span data-ttu-id="f283b-199">Všechny uložené procedury v databázi lze volat z F #.</span><span class="sxs-lookup"><span data-stu-id="f283b-199">Any stored procedures on the database can be called from F#.</span></span> <span data-ttu-id="f283b-200">Musíte nastavit statický parametr `StoredProcedures` k `true` v instance typu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="f283b-200">You must set the static parameter `StoredProcedures` to `true` in the type provider instantiation.</span></span> <span data-ttu-id="f283b-201">Typ zprostředkovatele `SqlDataConnection` obsahuje několik statických metod, které můžete použít ke konfiguraci typy, které se generují.</span><span class="sxs-lookup"><span data-stu-id="f283b-201">The type provider `SqlDataConnection` contains several static methods that you can use to configure the types that are generated.</span></span> <span data-ttu-id="f283b-202">Úplný popis těchto, najdete v části [sqldataconnection – zprostředkovatel typu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="f283b-202">For a complete description of these, see [SqlDataConnection Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span></span> <span data-ttu-id="f283b-203">Metoda na datový typ kontextu se generuje pro každou uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="f283b-203">A method on the data context type is generated for each stored procedure.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="f283b-204">Postup volání uložené procedury</span><span class="sxs-lookup"><span data-stu-id="f283b-204">To call a stored procedure</span></span>

<span data-ttu-id="f283b-205">Pokud uložené procedury přijímá parametry, které jsou s možnou hodnotou Null, je třeba předat odpovídající `System.Nullable` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f283b-205">If the stored procedures takes parameters that are nullable, you need to pass an appropriate `System.Nullable` value.</span></span> <span data-ttu-id="f283b-206">Návratová hodnota metody uložené procedury, která vrací skalární hodnota nebo tabulku je `System.Data.Linq.ISingleResult`, která obsahuje vlastnosti, které vám umožní přístup k vrácená data.</span><span class="sxs-lookup"><span data-stu-id="f283b-206">The return value of a stored procedure method that returns a scalar or a table is `System.Data.Linq.ISingleResult`, which contains properties that enable you to access the returned data.</span></span> <span data-ttu-id="f283b-207">Argument typu pro `System.Data.Linq.ISingleResult` závisí na konkrétní postup a je také jeden z typů, které generuje typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="f283b-207">The type argument for `System.Data.Linq.ISingleResult` depends on the specific procedure and is also one of the types that the type provider generates.</span></span> <span data-ttu-id="f283b-208">Pro uloženou proceduru s názvem `Procedure1`, typ je `Procedure1Result`.</span><span class="sxs-lookup"><span data-stu-id="f283b-208">For a stored procedure named `Procedure1`, the type is `Procedure1Result`.</span></span> <span data-ttu-id="f283b-209">Typ `Procedure1Result` obsahuje názvy sloupců v tabulce vrácené, nebo pro uložené procedury, jež vrací skalární hodnotu reprezentuje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f283b-209">The type `Procedure1Result` contains the names of the columns in a returned table, or, for a stored procedure that returns a scalar value, it represents the return value.</span></span>

<span data-ttu-id="f283b-210">Následující kód předpokládá, že je procedura `Procedure1` v databázi, která přijímá jako parametry dvě s možnou hodnotou Null celá čísla, spouští dotaz, který vrátí sloupec s názvem `TestData1`a vrátí celé číslo.</span><span class="sxs-lookup"><span data-stu-id="f283b-210">The following code assumes that there is a procedure `Procedure1` on the database that takes two nullable integers as parameters, runs a query that returns a column named `TestData1`, and returns an integer.</span></span>

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

## <a name="updating-the-database"></a><span data-ttu-id="f283b-211">Aktualizace databáze</span><span class="sxs-lookup"><span data-stu-id="f283b-211">Updating the database</span></span>
<span data-ttu-id="f283b-212">Typ LINQ DataContext obsahuje metody, které usnadňují provádět aktualizace databáze zpracovaných plně typové způsobem s generovaného typy.</span><span class="sxs-lookup"><span data-stu-id="f283b-212">The LINQ DataContext type contains methods that make it easier to perform transacted database updates in a fully typed fashion with the generated types.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="f283b-213">Postup aktualizace databáze</span><span class="sxs-lookup"><span data-stu-id="f283b-213">To update the database</span></span>

1. <span data-ttu-id="f283b-214">V následujícím kódu několik řádků se přidají do databáze.</span><span class="sxs-lookup"><span data-stu-id="f283b-214">In the following code, several rows are added to the database.</span></span> <span data-ttu-id="f283b-215">Pokud přidáváte jenom řádek, můžete použít `System.Data.Linq.Table.InsertOnSubmit()` k určení nového řádku přidat.</span><span class="sxs-lookup"><span data-stu-id="f283b-215">If you are only adding a row, you can use `System.Data.Linq.Table.InsertOnSubmit()` to specify the new row to add.</span></span> <span data-ttu-id="f283b-216">Při vkládání více řádků, je měli vložíte do kolekce a volání `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span><span class="sxs-lookup"><span data-stu-id="f283b-216">If you are inserting multiple rows, you should put them into a collection and call `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span></span> <span data-ttu-id="f283b-217">Při volání jedné z těchto metod, databáze není změnit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="f283b-217">When you call either of these methods, the database is not immediately changed.</span></span> <span data-ttu-id="f283b-218">Je třeba volat `System.Data.Linq.DataContext.SubmitChanges` skutečně provést změny.</span><span class="sxs-lookup"><span data-stu-id="f283b-218">You must call `System.Data.Linq.DataContext.SubmitChanges` to actually commit the changes.</span></span> <span data-ttu-id="f283b-219">Ve výchozím nastavení, vše, co můžete udělat předtím, než volání `System.Data.Linq.DataContext.SubmitChanges` je implicitně součástí stejné transakci.</span><span class="sxs-lookup"><span data-stu-id="f283b-219">By default, everything that you do before you call `System.Data.Linq.DataContext.SubmitChanges` is implicitly part of the same transaction.</span></span>

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

2. <span data-ttu-id="f283b-220">Nyní vyčistěte řádky voláním operace odstranění.</span><span class="sxs-lookup"><span data-stu-id="f283b-220">Now clean up the rows by calling a delete operation.</span></span>

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

## <a name="executing-transact-sql-code"></a><span data-ttu-id="f283b-221">Provádění kódu jazyka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f283b-221">Executing Transact-SQL code</span></span>
<span data-ttu-id="f283b-222">Transact-SQL můžete zadat také přímo pomocí `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` metodu `DataContext` třídy.</span><span class="sxs-lookup"><span data-stu-id="f283b-222">You can also specify Transact-SQL directly by using the `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` method on the `DataContext` class.</span></span>


#### <a name="to-execute-custom-sql-commands"></a><span data-ttu-id="f283b-223">K provedení vlastní příkazy SQL</span><span class="sxs-lookup"><span data-stu-id="f283b-223">To execute custom SQL commands</span></span>

<span data-ttu-id="f283b-224">Následující kód ukazuje, jak má odeslat příkazy SQL k vložení záznamu do tabulky a také k odstranění záznamu z tabulky.</span><span class="sxs-lookup"><span data-stu-id="f283b-224">The following code shows how to send SQL commands to insert a record into a table and also to delete a record from a table.</span></span>

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

## <a name="using-the-full-data-context"></a><span data-ttu-id="f283b-225">Pomocí kontextu úplné dat</span><span class="sxs-lookup"><span data-stu-id="f283b-225">Using the full data context</span></span>
<span data-ttu-id="f283b-226">V předchozích příkladech `GetDataContext` metoda byla použita k získání, co se nazývá *kontextu zjednodušené dat* pro schéma databáze.</span><span class="sxs-lookup"><span data-stu-id="f283b-226">In the previous examples, the `GetDataContext` method was used to get what is called the *simplified data context* for the database schema.</span></span> <span data-ttu-id="f283b-227">Kontext zjednodušené dat je snazší použijte, pokud jsou tvorbu dotazů, protože nejsou k dispozici jako mnoho členů.</span><span class="sxs-lookup"><span data-stu-id="f283b-227">The simplified data context is easier to use when you are constructing queries because there are not as many members available.</span></span> <span data-ttu-id="f283b-228">Proto při procházení vlastností v technologii IntelliSense, můžete se zaměřit na strukturu databáze, jako jsou tabulky a uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="f283b-228">Therefore, when you browse the properties in IntelliSense, you can focus on the database structure, such as the tables and stored procedures.</span></span> <span data-ttu-id="f283b-229">Je však omezení co můžete dělat s kontextem zjednodušené data.</span><span class="sxs-lookup"><span data-stu-id="f283b-229">However, there is a limit to what you can do with the simplified data context.</span></span> <span data-ttu-id="f283b-230">Úplná data kontextu, který poskytuje schopnost provádět další akce.</span><span class="sxs-lookup"><span data-stu-id="f283b-230">A full data context that provides the ability to perform other actions.</span></span> <span data-ttu-id="f283b-231">je také k dispozici je umístěný v `ServiceTypes` a má název *DataContext* statické parametr, pokud jste zadali ho.</span><span class="sxs-lookup"><span data-stu-id="f283b-231">is also available This is located in the `ServiceTypes` and has the name of the *DataContext* static parameter if you provided it.</span></span> <span data-ttu-id="f283b-232">Pokud není zadán ho, název typu kontextu dat vygeneruje pro vás SqlMetal.exe podle jiného vstupu.</span><span class="sxs-lookup"><span data-stu-id="f283b-232">If you did not provide it, the name of the data context type is generated for you by SqlMetal.exe based on the other input.</span></span> <span data-ttu-id="f283b-233">Úplná data kontextu dědí z `System.Data.Linq.DataContext` a zveřejňuje členy její základní třída, včetně odkazů na typy dat ADO.NET, jako `Connection` objektu, metody, jako `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` a `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` používané pro zápis dotazů v SQL, a také znamená pro práci s transakce explicitně.</span><span class="sxs-lookup"><span data-stu-id="f283b-233">The full data context inherits from `System.Data.Linq.DataContext` and exposes the members of its base class, including references to ADO.NET data types such as the `Connection` object, methods such as `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` and `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` that you can use to write queries in SQL, and also a means to work with transactions explicitly.</span></span>


#### <a name="to-use-the-full-data-context"></a><span data-ttu-id="f283b-234">Použití kontextu úplné dat</span><span class="sxs-lookup"><span data-stu-id="f283b-234">To use the full data context</span></span>

<span data-ttu-id="f283b-235">Následující kód ukazuje získání úplné datový objekt kontextu a pomocí příkazy přímo s databází.</span><span class="sxs-lookup"><span data-stu-id="f283b-235">The following code demonstrates getting a full data context object and using it to execute commands directly against the database.</span></span> <span data-ttu-id="f283b-236">V takovém případě jsou dva příkazy provádět v rámci stejné transakci.</span><span class="sxs-lookup"><span data-stu-id="f283b-236">In this case, two commands are executed as part of the same transaction.</span></span>

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

## <a name="deleting-data"></a><span data-ttu-id="f283b-237">Odstraňování dat</span><span class="sxs-lookup"><span data-stu-id="f283b-237">Deleting data</span></span>
<span data-ttu-id="f283b-238">Tento krok popisuje postup odstranění řádků z tabulky data.</span><span class="sxs-lookup"><span data-stu-id="f283b-238">This step shows you how to delete rows from a data table.</span></span>


#### <a name="to-delete-rows-from-the-database"></a><span data-ttu-id="f283b-239">Odstranění řádků z databáze</span><span class="sxs-lookup"><span data-stu-id="f283b-239">To delete rows from the database</span></span>

<span data-ttu-id="f283b-240">Nyní, vyčištění žádné přidány řádky napsáním funkci, která odstraní řádky ze zadané tabulky, instanci `System.Data.Linq.Table` třídy.</span><span class="sxs-lookup"><span data-stu-id="f283b-240">Now, clean up any added rows by writing a function that deletes rows from a specified table, an instance of the `System.Data.Linq.Table` class.</span></span> <span data-ttu-id="f283b-241">Pak zápis dotaz, který najde všechny řádky, které chcete odstranit a zřetězit výsledků dotazu do `deleteRows` funkce.</span><span class="sxs-lookup"><span data-stu-id="f283b-241">Then write a query to find all the rows that you want to delete, and pipe the results of the query into the `deleteRows` function.</span></span> <span data-ttu-id="f283b-242">Tento kód využívá schopnost poskytovat částečné aplikace argumenty funkce.</span><span class="sxs-lookup"><span data-stu-id="f283b-242">This code takes advantage of the ability to provide partial application of function arguments.</span></span>

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

## <a name="creating-a-test-database"></a><span data-ttu-id="f283b-243">Vytvoření databáze testu</span><span class="sxs-lookup"><span data-stu-id="f283b-243">Creating a test database</span></span>
<span data-ttu-id="f283b-244">V této části se dozvíte, jak nastavit testovací databáze pro použití v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="f283b-244">This section shows you how to set up the test database to use in this walkthrough.</span></span>

<span data-ttu-id="f283b-245">Všimněte si, že pokud změníte databázi nějakým způsobem, budete muset resetovat zprostředkovatel typu.</span><span class="sxs-lookup"><span data-stu-id="f283b-245">Note that if you alter the database in some way, you will have to reset the type provider.</span></span> <span data-ttu-id="f283b-246">Pokud chcete resetovat typ zprostředkovatele, znovu sestavit nebo vyčistit projekt, který obsahuje tohoto zprostředkovatele zadejte.</span><span class="sxs-lookup"><span data-stu-id="f283b-246">To reset the type provider, rebuild or clean the project that contains the type provider.</span></span>


#### <a name="to-create-the-test-database"></a><span data-ttu-id="f283b-247">Chcete-li vytvořit testovací databáze</span><span class="sxs-lookup"><span data-stu-id="f283b-247">To create the test database</span></span>

1. <span data-ttu-id="f283b-248">V **Průzkumníka serveru**, otevřete místní nabídku pro **připojení dat** uzel a zvolte **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="f283b-248">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and choose **Add Connection**.</span></span> <span data-ttu-id="f283b-249">**Přidat připojení** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f283b-249">The **Add Connection** dialog box appears.</span></span>

2. <span data-ttu-id="f283b-250">V **název serveru** pole, zadejte název instance systému SQL Server, ke které máte přístup pro správu nebo pokud nemáte přístup k serveru, zadejte (localdb\v11.0).</span><span class="sxs-lookup"><span data-stu-id="f283b-250">In the **Server name** box, specify the name of an instance of SQL Server that you have administrative access to, or if you do not have access to a server, specify (localdb\v11.0).</span></span> <span data-ttu-id="f283b-251">SQL Express LocalDB poskytuje odlehčený databázový server pro vývoj a testování v počítači.</span><span class="sxs-lookup"><span data-stu-id="f283b-251">SQL Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="f283b-252">Vytvoří se nový uzel v **Průzkumníka serveru** pod **datová připojení**.</span><span class="sxs-lookup"><span data-stu-id="f283b-252">A new node is created in **Server Explorer** under **Data Connections**.</span></span> <span data-ttu-id="f283b-253">Další informace o LocalDB najdete v tématu [návod: Vytvoření místního souboru databáze v sadě Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span><span class="sxs-lookup"><span data-stu-id="f283b-253">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>

3. <span data-ttu-id="f283b-254">Otevřete místní nabídku pro nový uzel připojení a vyberte **nový dotaz**.</span><span class="sxs-lookup"><span data-stu-id="f283b-254">Open the shortcut menu for the new connection node, and select **New Query**.</span></span>

4. <span data-ttu-id="f283b-255">Zkopírujte následující skript SQL, vložte jej do editoru dotazů a potom zvolte **Execute** tlačítka na panelu nástrojů nebo zvolte klávesy Ctrl + Shift + E.</span><span class="sxs-lookup"><span data-stu-id="f283b-255">Copy the following SQL script, paste it into the query editor, and then choose the **Execute** button on the toolbar or choose the Ctrl+Shift+E keys.</span></span>

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


## <a name="see-also"></a><span data-ttu-id="f283b-256">Viz také</span><span class="sxs-lookup"><span data-stu-id="f283b-256">See Also</span></span>
[<span data-ttu-id="f283b-257">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="f283b-257">Type Providers</span></span>](index.md)

[<span data-ttu-id="f283b-258">Sqldataconnection – zprostředkovatel typu</span><span class="sxs-lookup"><span data-stu-id="f283b-258">SqlDataConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[<span data-ttu-id="f283b-259">Návod: Generování typů F # ze souboru DBML</span><span class="sxs-lookup"><span data-stu-id="f283b-259">Walkthrough: Generating F# Types from a DBML File</span></span>](generating-fsharp-types-from-dbml.md)

[<span data-ttu-id="f283b-260">Výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="f283b-260">Query Expressions</span></span>](../../language-reference/query-expressions.md)

[<span data-ttu-id="f283b-261">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f283b-261">LINQ to SQL</span></span>](../../../../docs/framework/data/adonet/sql/linq/index.md)

[<span data-ttu-id="f283b-262">SqlMetal.exe &#40; Nástroj pro vytváření kódu &#41;</span><span class="sxs-lookup"><span data-stu-id="f283b-262">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)
