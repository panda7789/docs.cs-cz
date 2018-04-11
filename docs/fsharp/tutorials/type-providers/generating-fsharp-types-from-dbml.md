---
title: 'Návod: Generování typů F# ze souboru DBML (F#)'
description: 'Informace o vytvoření typů F # pro data z databáze v F # 3.0, pokud máte v souboru DBML kódování informace o schématu.'
keywords: 'Visual f #, f #, funkční programování'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: 3cd8df9becac0d1a8842eb22e2f772eee6307acf
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a><span data-ttu-id="d528e-104">Návod: Generování typů F# ze souboru DBML</span><span class="sxs-lookup"><span data-stu-id="d528e-104">Walkthrough: Generating F# Types from a DBML File</span></span>

> [!NOTE]
<span data-ttu-id="d528e-105">Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="d528e-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="d528e-106">V tématu [FSharp.Data](https://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="d528e-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="d528e-107">Rozhraní API referenčních odkazů se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="d528e-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="d528e-108">Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="d528e-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="d528e-109">Tento názorný postup pro F # 3.0 popisuje postup vytvoření typů dat z databáze, pokud máte v souboru DBML kódování informace o schématu.</span><span class="sxs-lookup"><span data-stu-id="d528e-109">This walkthrough for F# 3.0 describes how to create types for data from a database when you have schema information encoded in a .dbml file.</span></span> <span data-ttu-id="d528e-110">Technologie LINQ to SQL používá k reprezentaci schéma databáze tohoto formátu souboru.</span><span class="sxs-lookup"><span data-stu-id="d528e-110">LINQ to SQL uses this file format to represent database schema.</span></span> <span data-ttu-id="d528e-111">Technologie LINQ to SQL souboru schématu v sadě Visual Studio můžete vygenerovat pomocí Návrhář relací objektů (relací objektů).</span><span class="sxs-lookup"><span data-stu-id="d528e-111">You can generate a LINQ to SQL schema file in Visual Studio by using the Object Relational (O/R) Designer.</span></span> <span data-ttu-id="d528e-112">Další informace najdete v tématu [přehled Návrhář relací objektů](https://msdn.microsoft.com/library/bb384511.aspx) a [generování kódu v technologii LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="d528e-112">For more information, see [O/R Designer Overview](https://msdn.microsoft.com/library/bb384511.aspx) and [Code Generation in LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>

<span data-ttu-id="d528e-113">Typ zprostředkovatele databáze Markup Language (DBML) umožňuje psát kód, který používá typy podle schématu databáze, aniž by bylo potřeba zadat statické připojovací řetězec v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="d528e-113">The Database Markup Language (DBML) type provider allows you to write code that uses types based on a database schema without requiring you to specify a static connection string at compile time.</span></span> <span data-ttu-id="d528e-114">Který může být užitečné, pokud je potřeba povolit možnost, že poslední aplikace bude používat jiné databázi, jiné přihlašovací údaje nebo jiné připojovací řetězec než ten, který použijete k vývoji aplikace.</span><span class="sxs-lookup"><span data-stu-id="d528e-114">That can be useful if you need to allow for the possibility that the final application will use a different database, different credentials, or a different connection string than the one you use to develop the application.</span></span> <span data-ttu-id="d528e-115">Pokud máte připojení k databázi direct, který můžete použít při kompilaci a jedná se o stejné databáze a přihlašovacích údajů, které bude nakonec použijete v integrované aplikaci, můžete taky sqldataconnection – zprostředkovatel typu.</span><span class="sxs-lookup"><span data-stu-id="d528e-115">If you have a direct database connection that you can use at compile time and this is the same database and credentials that you will eventually use in your built application, you can also use the SQLDataConnection type provider.</span></span> <span data-ttu-id="d528e-116">Další informace najdete v tématu [návod: přístup k databázi SQL pomocí zprostředkovatelé typu](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="d528e-116">For more information, see [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>

<span data-ttu-id="d528e-117">Tento návod ukazuje následující úlohy.</span><span class="sxs-lookup"><span data-stu-id="d528e-117">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="d528e-118">Mají být provedeny v uvedeném pořadí návod úspěšné:</span><span class="sxs-lookup"><span data-stu-id="d528e-118">They should be completed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="d528e-119">Vytvoření souboru DBML</span><span class="sxs-lookup"><span data-stu-id="d528e-119">Creating a .dbml file</span></span>
<br />

- <span data-ttu-id="d528e-120">Vytvoření a nastavení projektu F #</span><span class="sxs-lookup"><span data-stu-id="d528e-120">Creating and setting up an F# project</span></span>
<br />

- <span data-ttu-id="d528e-121">Konfigurace zprostředkovatele typů a generování typy</span><span class="sxs-lookup"><span data-stu-id="d528e-121">Configuring the type provider and generating the types</span></span>
<br />

- <span data-ttu-id="d528e-122">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="d528e-122">Querying the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="d528e-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d528e-123">Prerequisites</span></span>

## <a name="creating-a-dbml-file"></a><span data-ttu-id="d528e-124">Vytvoření souboru DBML</span><span class="sxs-lookup"><span data-stu-id="d528e-124">Creating a .dbml file</span></span>
<span data-ttu-id="d528e-125">Pokud nemáte k testování v databázi, vytvořit podle pokynů uvedených v dolní části [návod: přístup k databázi SQL pomocí zprostředkovatelé typu](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="d528e-125">If you do not have a database to test on, create one by following the instructions at the bottom of [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span> <span data-ttu-id="d528e-126">Pokud budete postupovat podle těchto pokynů, vytvoříte databázi názvem databáze, která obsahuje několik jednoduchých tabulek a uložených procedur v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d528e-126">If you follow these instructions, you will create a database called MyDatabase that contains a few simple tables and stored procedures on your SQL Server.</span></span>

<span data-ttu-id="d528e-127">Pokud již máte soubor DBML, můžete přeskočit k části **vytvořit a nastavit si F # projekt**.</span><span class="sxs-lookup"><span data-stu-id="d528e-127">If you already have a .dbml file, you can skip to the section, **Create and Set Up an F# Project**.</span></span> <span data-ttu-id="d528e-128">Jinak můžete vytvořit soubor DBML danou existující databázi SQL a pomocí příkazového řádku nástroje SqlMetal.exe.</span><span class="sxs-lookup"><span data-stu-id="d528e-128">Otherwise, you can create a .dbml file given an existing SQL database and by using the command-line tool SqlMetal.exe.</span></span>


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a><span data-ttu-id="d528e-129">Vytvoření souboru DBML pomocí SqlMetal.exe</span><span class="sxs-lookup"><span data-stu-id="d528e-129">To create a .dbml file by using SqlMetal.exe</span></span>

1. <span data-ttu-id="d528e-130">Otevřete **příkazový řádek vývojáře**.</span><span class="sxs-lookup"><span data-stu-id="d528e-130">Open a **Developer Command Prompt**.</span></span>
<br />

2. <span data-ttu-id="d528e-131">Zajistěte, abyste měli přístup k SqlMetal.exe zadáním `SqlMetal.exe /?` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="d528e-131">Ensure that you have access to SqlMetal.exe by entering `SqlMetal.exe /?` at the command prompt.</span></span> <span data-ttu-id="d528e-132">SqlMetal.exe je obvykle nainstalovaný v části **Microsoft SDKs** složky v **Program Files** nebo **Program Files (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d528e-132">SqlMetal.exe is typically installed under the **Microsoft SDKs** folder in **Program Files** or **Program Files (x86)**.</span></span>
<br />

3. <span data-ttu-id="d528e-133">Spusťte SqlMetal.exe s následujících možností příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d528e-133">Run SqlMetal.exe with the following command-line options.</span></span> <span data-ttu-id="d528e-134">Nahraďte správnou cestu místě `c:\destpath` pro vytvoření souboru dbml a vkládání odpovídající hodnoty pro databázový server, instanci název a název databáze.</span><span class="sxs-lookup"><span data-stu-id="d528e-134">Substitute an appropriate path in place of `c:\destpath` to create the .dbml file, and insert appropriate values for the database server, instance name, and database name.</span></span>
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
<span data-ttu-id="d528e-135">Pokud SqlMetal.exe má potíže při vytváření souboru problémy s oprávněními, změňte do složky, ke které máte oprávnění k zápisu do aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="d528e-135">If SqlMetal.exe has trouble creating the file due to permissions issues, change the current directory to a folder that you have write access to.</span></span>


4. <span data-ttu-id="d528e-136">Můžete také prohlédnout další dostupné možnosti příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d528e-136">You can also look at the other available command-line options.</span></span> <span data-ttu-id="d528e-137">Například jsou možnosti, které můžete použít, pokud chcete, zobrazení a funkcí SQL, které jsou součástí generovaného typy.</span><span class="sxs-lookup"><span data-stu-id="d528e-137">For example, there are options you can use if you want views and SQL functions included in the generated types.</span></span> <span data-ttu-id="d528e-138">Další informace najdete v tématu [SqlMetal.exe &#40;nástroj pro vytváření kódu&#41;](https://msdn.microsoft.com/library/bb386987).</span><span class="sxs-lookup"><span data-stu-id="d528e-138">For more information, see [SqlMetal.exe &#40;Code Generation Tool&#41;](https://msdn.microsoft.com/library/bb386987).</span></span>
<br />


## <a name="creating-and-setting-up-an-f-project"></a><span data-ttu-id="d528e-139">Vytvoření a nastavení projektu F #</span><span class="sxs-lookup"><span data-stu-id="d528e-139">Creating and setting up an F# project</span></span>
<span data-ttu-id="d528e-140">V tomto kroku vytvořte projekt a přidejte příslušné odkazy na použití DBML typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="d528e-140">In this step, you create a project and add appropriate references to use the DBML type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="d528e-141">Postup vytvoření a nastavení projektu jazyka F#</span><span class="sxs-lookup"><span data-stu-id="d528e-141">To create and set up an F# project</span></span>

1. <span data-ttu-id="d528e-142">Přidáte nový projekt konzolové aplikace v F # do řešení.</span><span class="sxs-lookup"><span data-stu-id="d528e-142">Add a new F# Console Application project to your solution.</span></span>
<br />

2. <span data-ttu-id="d528e-143">V **Průzkumníku řešení**, otevřete místní nabídku pro **odkazy**a potom zvolte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="d528e-143">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="d528e-144">V **sestavení** oblasti, vyberte **Framework** uzel a potom v seznamu dostupných sestavení, vyberte **System.Data** a **System.Data.Linq**  sestavení.</span><span class="sxs-lookup"><span data-stu-id="d528e-144">In the **Assemblies** area, choose the **Framework** node, and then, in the list of available assemblies, choose the **System.Data** and **System.Data.Linq** assemblies.</span></span>
<br />

4. <span data-ttu-id="d528e-145">V **sestavení** oblasti, zvolte **rozšíření**a potom v seznamu dostupných sestavení, zvolte **FSharp.Data.TypeProviders**.</span><span class="sxs-lookup"><span data-stu-id="d528e-145">In the **Assemblies** area, choose **Extensions**, and then, in the list of available assemblies, choose **FSharp.Data.TypeProviders**.</span></span>
<br />

5. <span data-ttu-id="d528e-146">Vyberte **OK** tlačítko přidáte odkazy na tyto sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="d528e-146">Choose the **OK** button to add references to these assemblies to your project.</span></span>
<br />

6. <span data-ttu-id="d528e-147">(Volitelné).</span><span class="sxs-lookup"><span data-stu-id="d528e-147">(Optional).</span></span> <span data-ttu-id="d528e-148">Zkopírujte dbml soubor, který jste vytvořili v předchozím kroku a vložte soubor ve složce hlavní pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="d528e-148">Copy the .dbml file that you created in the previous step, and paste the file in the main folder for your project.</span></span> <span data-ttu-id="d528e-149">Tato složka obsahuje soubor projektu (.fsproj) a soubory kódu.</span><span class="sxs-lookup"><span data-stu-id="d528e-149">This folder contains the project file (.fsproj) and code files.</span></span> <span data-ttu-id="d528e-150">Na řádku nabídek zvolte **projektu**, **přidat existující položku**a pak zadejte souboru DBML ho přidejte do projektu.</span><span class="sxs-lookup"><span data-stu-id="d528e-150">On the menu bar, choose **Project**, **Add Existing Item**, and then specify the .dbml file to add it to your project.</span></span> <span data-ttu-id="d528e-151">Pokud tyto kroky dokončíte, můžete vynechat statický parametr resolutionfolder – v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="d528e-151">If you complete these steps, you can omit the ResolutionFolder static parameter in the next step.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="d528e-152">Konfigurace poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="d528e-152">Configuring the type provider</span></span>
<span data-ttu-id="d528e-153">V této části vytvoříte zprostředkovatele typů a generovat typy ze schématu, která je popsána v souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="d528e-153">In this section, you create a type provider and generate types from the schema that’s described in the .dbml file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a><span data-ttu-id="d528e-154">Ke konfiguraci poskytovatele za typ a generování typy</span><span class="sxs-lookup"><span data-stu-id="d528e-154">To configure the type provider and generate the types</span></span>

- <span data-ttu-id="d528e-155">Přidejte kód, který otevře **TypeProviders** obor názvů a vytvoří instanci zprostředkovatele typu DBML souboru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="d528e-155">Add code that opens the **TypeProviders** namespace and instantiates the type provider for the .dbml file that you want to use.</span></span> <span data-ttu-id="d528e-156">Pokud jste přidali soubor DBML do projektu, můžete vynechat statický parametr resolutionfolder –.</span><span class="sxs-lookup"><span data-stu-id="d528e-156">If you added the .dbml file to your project, you can omit the ResolutionFolder static parameter.</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

<span data-ttu-id="d528e-157">Typ DataContext poskytuje přístup k všechny vygenerované typy a dědí z `System.Data.Linq.DataContext`.</span><span class="sxs-lookup"><span data-stu-id="d528e-157">The DataContext type provides access to all the generated types and inherits from `System.Data.Linq.DataContext`.</span></span> <span data-ttu-id="d528e-158">Dbmlfile – poskytovatel typů má různých statických parametry, které můžete nastavit.</span><span class="sxs-lookup"><span data-stu-id="d528e-158">The DbmlFile type provider has various static parameters that you can set.</span></span> <span data-ttu-id="d528e-159">Například můžete použít jiný název pro typ DataContext zadáním `DataContext=MyDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d528e-159">For example, you can use a different name for the DataContext type by specifying `DataContext=MyDataContext`.</span></span> <span data-ttu-id="d528e-160">V takovém případě kódu podobá následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="d528e-160">In that case, your code resembles the following example:</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a><span data-ttu-id="d528e-161">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="d528e-161">Querying the database</span></span>
<span data-ttu-id="d528e-162">V této části použijete F # – výrazy dotazů k dotazování databáze.</span><span class="sxs-lookup"><span data-stu-id="d528e-162">In this section, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="d528e-163">Postup dotazování na data</span><span class="sxs-lookup"><span data-stu-id="d528e-163">To query the data</span></span>

- <span data-ttu-id="d528e-164">Přidáte kód pro dotazování databáze.</span><span class="sxs-lookup"><span data-stu-id="d528e-164">Add code to query the database.</span></span>
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a><span data-ttu-id="d528e-165">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d528e-165">Next Steps</span></span>
<span data-ttu-id="d528e-166">Můžete pokračovat pro ostatní výrazy dotazu nebo získání připojení k databázi z kontextu dat a provádět běžné operace dat ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="d528e-166">You can proceed to use other query expressions, or get a database connection from the data context and perform normal ADO.NET data operations.</span></span> <span data-ttu-id="d528e-167">Další kroky, najdete v částech po "dotazu Data" v [návod: přístup k databázi SQL pomocí zprostředkovatelé typu](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="d528e-167">For additional steps, see the sections after "Query the Data" in [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="d528e-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="d528e-168">See Also</span></span>
[<span data-ttu-id="d528e-169">Dbmlfile – zprostředkovatel typu</span><span class="sxs-lookup"><span data-stu-id="d528e-169">DbmlFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="d528e-170">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="d528e-170">Type Providers</span></span>](index.md)

[<span data-ttu-id="d528e-171">Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="d528e-171">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>](accessing-a-sql-database.md)

[<span data-ttu-id="d528e-172">SqlMetal.exe &#40;nástroj pro vytváření kódu&#41;</span><span class="sxs-lookup"><span data-stu-id="d528e-172">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)

[<span data-ttu-id="d528e-173">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="d528e-173">Query Expressions</span></span>](../../language-reference/query-expressions.md)
