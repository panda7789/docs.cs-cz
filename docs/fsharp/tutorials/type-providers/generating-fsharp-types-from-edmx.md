---
title: "Návod: Generování typů F# ze souboru schématu EDMX (F#)"
description: "Informace o vytvoření typů F # pro data reprezentované podle Data modelu Entity (EDM) v F # 3.0, kde je v souboru EDMX zadané schéma."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 5c59911f5f880493080ef1838bc015045ce4336a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a><span data-ttu-id="12e13-104">Návod: Generování typů F# ze souboru schématu EDMX</span><span class="sxs-lookup"><span data-stu-id="12e13-104">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>

> [!NOTE]
<span data-ttu-id="12e13-105">Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="12e13-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="12e13-106">V tématu [FSharp.Data](http://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="12e13-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="12e13-107">Rozhraní API referenčních odkazů se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="12e13-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="12e13-108">Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="12e13-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="12e13-109">Tento návod pro jazyk F# 3.0 popisuje způsob vytváření typů pro data reprezentovaná modelem Entity Data Model (EDM), jehož schéma je zadáno v souboru .edmx.</span><span class="sxs-lookup"><span data-stu-id="12e13-109">This walkthrough for F# 3.0 shows you how to create types for data that is represented by the Entity Data Model (EDM), the schema for which is specified in an .edmx file.</span></span> <span data-ttu-id="12e13-110">Tento návod znázorňuje také způsob používání poskytovatele typu EdmxFile.</span><span class="sxs-lookup"><span data-stu-id="12e13-110">This walkthrough also shows how to use the EdmxFile type provider.</span></span> <span data-ttu-id="12e13-111">Než začnete, zvažte, zda není vhodnější poskytovatel typu SqlEntityConnection.</span><span class="sxs-lookup"><span data-stu-id="12e13-111">Before you begin, consider whether a SqlEntityConnection type provider is a more appropriate type provider option.</span></span> <span data-ttu-id="12e13-112">Poskytovatel typu SqlEntityConnection funguje nejlépe v situacích, kdy je k dispozici online databáze, ke které se lze připojit během vývojové fáze projektu, a nevadí vám zadávání připojovacího řetězce v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="12e13-112">The SqlEntityConnection type provider works best for scenarios where you have a live database that you can connect to during the development phase of your project, and you do not mind specifying the connection string at compile time.</span></span> <span data-ttu-id="12e13-113">Tento poskytovatel typu je však omezen tím, že neposkytuje tolik funkcí databáze jako poskytovatel typu EdmxFile.</span><span class="sxs-lookup"><span data-stu-id="12e13-113">However, this type provider is also limited in that it doesn't expose as much database functionality as the EdmxFile type provider.</span></span> <span data-ttu-id="12e13-114">Dále platí, že pokud pro projekt databáze, který používá model Entity Data Model, nemáte připojení k online databázi, můžete pro kód databáze použít soubor .edmx.</span><span class="sxs-lookup"><span data-stu-id="12e13-114">Also, if you don't have a live database connection for a database project that uses the Entity Data Model, you can use the .edmx file to code against the database.</span></span> <span data-ttu-id="12e13-115">Pokud použijete poskytovatele typu EdmxFile, kompilátor jazyka F# spustí program EdmGen.exe a vygeneruje poskytované typy.</span><span class="sxs-lookup"><span data-stu-id="12e13-115">When you use the EdmxFile type provider, the F# compiler runs EdmGen.exe to generate the types that it provides.</span></span>

<span data-ttu-id="12e13-116">Tento návod znázorňuje následující úkoly, které je nutné z důvodu správné funkčnosti provést v tomto pořadí:</span><span class="sxs-lookup"><span data-stu-id="12e13-116">This walkthrough illustrates the following tasks, which you must perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="12e13-117">Vytvoření souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="12e13-117">Creating an EDMX file</span></span>
<br />

- <span data-ttu-id="12e13-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="12e13-118">Creating the project</span></span>
<br />

- <span data-ttu-id="12e13-119">Hledání nebo vytváření entity data model připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="12e13-119">Finding or creating the entity data model connection string</span></span>
<br />

- <span data-ttu-id="12e13-120">Konfigurace poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="12e13-120">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="12e13-121">Dotazování na data</span><span class="sxs-lookup"><span data-stu-id="12e13-121">Querying the data</span></span>
<br />

- <span data-ttu-id="12e13-122">Volání uložené procedury</span><span class="sxs-lookup"><span data-stu-id="12e13-122">Calling a stored procedure</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="12e13-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12e13-123">Prerequisites</span></span>

## <a name="creating-an-edmx-file"></a><span data-ttu-id="12e13-124">Vytvoření souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="12e13-124">Creating an EDMX file</span></span>
<span data-ttu-id="12e13-125">Pokud již máte soubor EDMX, můžete tento krok přeskočit.</span><span class="sxs-lookup"><span data-stu-id="12e13-125">If you already have an EDMX file, you can skip this step.</span></span>


#### <a name="to-create-an-edmx-file"></a><span data-ttu-id="12e13-126">Postup vytvoření souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="12e13-126">To create an EDMX file</span></span>

- <span data-ttu-id="12e13-127">Pokud již nemáte souboru EDMX, můžete postupovat podle pokynů na konci tohoto názorného postupu v kroku [konfiguraci datového modelu Entity](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span><span class="sxs-lookup"><span data-stu-id="12e13-127">If you don't already have an EDMX file, you can follow the instructions at the end of this walkthrough in the step [Configuring the Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span></span>
<br />

## <a name="creating-the-project"></a><span data-ttu-id="12e13-128">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="12e13-128">Creating the project</span></span>
<span data-ttu-id="12e13-129">V tomto kroku vytvoříte projekt a přidáte do něj příslušné odkazy, které jsou vyžadovány pro používání poskytovatele typu EDMX.</span><span class="sxs-lookup"><span data-stu-id="12e13-129">In this step, you create a project and add appropriate references to it to use the EDMX type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="12e13-130">Postup vytvoření a nastavení projektu jazyka F#</span><span class="sxs-lookup"><span data-stu-id="12e13-130">To create and set up an F# project</span></span>

1. <span data-ttu-id="12e13-131">Ukončete předchozí projekt, vytvořte nový projekt a zadejte název SchoolEDM.</span><span class="sxs-lookup"><span data-stu-id="12e13-131">Close the previous project, create another project, and name it SchoolEDM.</span></span>
<br />

2. <span data-ttu-id="12e13-132">V **Průzkumníku řešení**, otevřete místní nabídku pro **odkazy**a potom zvolte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="12e13-132">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="12e13-133">V **sestavení** oblasti, vyberte **Framework** uzlu.</span><span class="sxs-lookup"><span data-stu-id="12e13-133">In the **Assemblies** area, choose the **Framework** node.</span></span>
<br />

4. <span data-ttu-id="12e13-134">V seznamu dostupných sestavení, vyberte **System.Data.Entity** a **System.Data.Linq** sestavení a potom zvolte **přidat** tlačítko přidáte odkazy na tyto sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="12e13-134">In the list of available assemblies, choose the **System.Data.Entity** and **System.Data.Linq** assemblies, and then choose the **Add** button to add references to these assemblies to your project.</span></span>
<br />

5. <span data-ttu-id="12e13-135">V **sestavení** oblasti, vyberte **rozšíření** uzlu.</span><span class="sxs-lookup"><span data-stu-id="12e13-135">In the **Assemblies** area, select the **Extensions** node.</span></span>
<br />

6. <span data-ttu-id="12e13-136">V seznamu dostupných rozšíření přidejte odkaz na sestavení FSharp.Data.TypeProviders.</span><span class="sxs-lookup"><span data-stu-id="12e13-136">In the  list of available extensions, add a reference to the FSharp.Data.TypeProviders assembly.</span></span>
<br />

7. <span data-ttu-id="12e13-137">Otevřete příslušné obory názvů přidáním následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="12e13-137">Add the following code to open the appropriate namespaces.</span></span>
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="12e13-138">Vyhledání nebo vytvoření připojovacího řetězce pro model Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="12e13-138">Finding or creating the connection string for the Entity Data Model</span></span>
<span data-ttu-id="12e13-139">Připojovací řetězec modelu Entity Data Model (připojovací řetězec EDMX) zahrnuje nejen připojovací řetězec poskytovatele databáze, ale také další informace.</span><span class="sxs-lookup"><span data-stu-id="12e13-139">The connection string for the Entity Data Model (EDMX connection string) includes not only the connection string for the database provider but also additional information.</span></span> <span data-ttu-id="12e13-140">Například připojovací řetězec EDMX pro jednotlivou databázi SQL Server připomíná následující kód.</span><span class="sxs-lookup"><span data-stu-id="12e13-140">For example, EDMX connection string for a simple SQL Server database resembles the following code.</span></span>

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

<span data-ttu-id="12e13-141">Další informace o připojovacích řetězcích EDMX najdete v tématu [připojovací řetězce](https://msdn.microsoft.com/library/ms254494.aspx).</span><span class="sxs-lookup"><span data-stu-id="12e13-141">For more information about EDMX connection strings, see [Connection Strings](https://msdn.microsoft.com/library/ms254494.aspx).</span></span>


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="12e13-142">Postup vyhledání nebo vytvoření připojovacího řetězce modelu Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="12e13-142">To find or create the connection string for the Entity Data Model</span></span>

1. <span data-ttu-id="12e13-143">Ruční generování připojovacích řetězců EDMX může být obtížné. Programovým generováním ušetříte čas.</span><span class="sxs-lookup"><span data-stu-id="12e13-143">EDMX connection strings can be difficult to generate by hand, so you can save time by generating it programmatically.</span></span> <span data-ttu-id="12e13-144">Pokud již připojovací řetězec EDMX znáte, můžete tento krok přeskočit a použít tento řetězec v následujícím kroku.</span><span class="sxs-lookup"><span data-stu-id="12e13-144">If you know your EDMX connection string, you can bypass this step and simply use that string in the next step.</span></span> <span data-ttu-id="12e13-145">Pokud řetězec neznáte, použijte následující kód pro vygenerování připojovacího řetězce EDMX z poskytovaného připojovacího řetězce databáze.</span><span class="sxs-lookup"><span data-stu-id="12e13-145">If not, use the following code to generate the EDMX connection string from a database connection string that you provide.</span></span>
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a><span data-ttu-id="12e13-146">Konfigurace poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="12e13-146">Configuring the type provider</span></span>
<span data-ttu-id="12e13-147">V tomto kroku vytvoříte a nakonfigurujete poskytovatele typu s připojovacím řetězcem EDMX a vygenerujete typy schématu, které je definováno v souboru .edmx.</span><span class="sxs-lookup"><span data-stu-id="12e13-147">In this step, you create and configure the type provider with the EDMX connection string, and you generate types for the schema that's defined in the .edmx file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="12e13-148">Postup konfigurace poskytovatele typu a generování typů</span><span class="sxs-lookup"><span data-stu-id="12e13-148">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="12e13-149">Zkopírujte soubor .edmx vygenerovaný v prvním kroku tohoto návodu do složky projektu.</span><span class="sxs-lookup"><span data-stu-id="12e13-149">Copy the .edmx file that you generated in the first step of this walkthrough to your project folder.</span></span>
<br />

2. <span data-ttu-id="12e13-150">Zvolte otevřete místní nabídce uzlu projektu v projektu F # **přidat existující položku**a potom zvolte soubor EDMX ho přidejte do projektu.</span><span class="sxs-lookup"><span data-stu-id="12e13-150">Open the shortcut menu for the project node in your F# project, choose **Add Existing Item**, and then choose the .edmx file to add it to your project.</span></span>
<br />

3. <span data-ttu-id="12e13-151">Aktivujte poskytovatele typu pro soubor .edmx zadáním následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="12e13-151">Enter the following code to activate the type provider for your .edmx file.</span></span> <span data-ttu-id="12e13-152">Nahraďte *Server*\*Instance * s názvem serveru, který používá SQL Server a název instance a použít název souboru EDMX z první krok v tomto průvodci.</span><span class="sxs-lookup"><span data-stu-id="12e13-152">Replace *Server*\*Instance* with the name of your server that's running SQL Server and the name of your instance, and use the name of your .edmx file from the first step in this walkthrough.</span></span>
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a><span data-ttu-id="12e13-153">Dotazování na data</span><span class="sxs-lookup"><span data-stu-id="12e13-153">Querying the data</span></span>
<span data-ttu-id="12e13-154">V tomto kroku použijete výrazy dotazů jazyka F# pro zadávání dotazů na databázi.</span><span class="sxs-lookup"><span data-stu-id="12e13-154">In this step, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="12e13-155">Postup dotazování na data</span><span class="sxs-lookup"><span data-stu-id="12e13-155">To query the data</span></span>

- <span data-ttu-id="12e13-156">Chcete-li zadat dotaz na data v modelu Entity Data Model, použijte následující kód.</span><span class="sxs-lookup"><span data-stu-id="12e13-156">Enter the following code to query the data in the entity data model.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="12e13-157">Volání uložené procedury</span><span class="sxs-lookup"><span data-stu-id="12e13-157">Calling a stored procedure</span></span>
<span data-ttu-id="12e13-158">Uložené procedury lze volat pomocí poskytovatele typu EDMX.</span><span class="sxs-lookup"><span data-stu-id="12e13-158">You can call stored procedures by using the EDMX type provider.</span></span> <span data-ttu-id="12e13-159">V následujícím postupu školní databáze obsahuje uložené procedury, **UpdatePerson**, jaké aktualizace se záznam dané nové hodnoty pro sloupce.</span><span class="sxs-lookup"><span data-stu-id="12e13-159">In the following procedure, the School database contains a stored procedure, **UpdatePerson**, which updates a record, given new values for the columns.</span></span> <span data-ttu-id="12e13-160">Tuto uloženou proceduru můžete použít, protože je vystavena jako metoda v typu DataContext.</span><span class="sxs-lookup"><span data-stu-id="12e13-160">You can use this stored procedure because it's exposed as a method on the DataContext type.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="12e13-161">Postup volání uložené procedury</span><span class="sxs-lookup"><span data-stu-id="12e13-161">To call a stored procedure</span></span>

- <span data-ttu-id="12e13-162">Aktualizujte záznamy přidáním následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="12e13-162">Add the following code to update records.</span></span>
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

<span data-ttu-id="12e13-163">V případě úspěchu je výsledek 1.</span><span class="sxs-lookup"><span data-stu-id="12e13-163">The result is 1 if you succeed.</span></span> <span data-ttu-id="12e13-164">Všimněte si, že **exactlyOne** se používá ve výrazu dotazu k zajištění, že pouze jeden výsledek vrácený; jinak hodnota, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="12e13-164">Notice that **exactlyOne** is used in the query expression to ensure that only one result is returned; otherwise, an exception is thrown.</span></span> <span data-ttu-id="12e13-165">Navíc pokud chcete snadno pracovat s hodnotami Null, můžete použít jednoduchý **s možnou hodnotou Null** funkce, která je definována v tento kód vytvořit hodnotu Null mimo obyčejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="12e13-165">Also, to work with nullable values more easily, you can use the simple **nullable** function that's defined in this code to create a nullable value out of an ordinary value.</span></span>

<br />

## <a name="configuring-the-entity-data-model"></a><span data-ttu-id="12e13-166">Konfigurace modelu Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="12e13-166">Configuring the Entity Data Model</span></span>
<span data-ttu-id="12e13-167">Tento postup byste měli dokončit pouze v případě, že chcete vědět, jak lze vygenerovat úplný model Entity Data Model z databáze, není-li k dispozici databáze pro testování.</span><span class="sxs-lookup"><span data-stu-id="12e13-167">You should complete this procedure only if you want to know how to generate a full Entity Data Model from a database and you don't have a database with which to test.</span></span>


#### <a name="to-configure-the-entity-data-model"></a><span data-ttu-id="12e13-168">Postup konfigurace modelu Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="12e13-168">To configure the Entity Data Model</span></span>

1. <span data-ttu-id="12e13-169">Na řádku nabídek zvolte **SQL**, **editoru jazyka Transact-SQL**, **nový dotaz** k vytvoření databáze.</span><span class="sxs-lookup"><span data-stu-id="12e13-169">On the menu bar, choose **SQL**, **Transact-SQL Editor**, **New Query** to create a database.</span></span> <span data-ttu-id="12e13-170">Budete-li k tomu vyzváni, zadejte server a instanci databáze.</span><span class="sxs-lookup"><span data-stu-id="12e13-170">If prompted, specify your database server and instance.</span></span>
<br />

2. <span data-ttu-id="12e13-171">Zkopírujte a vložte obsah skriptu databáze, který vytvoří databázi studenty, jak je popsáno v [dokumentaci k rozhraní Entity Framework](http://msdn.microsoft.com/data/JJ614587.aspx) v datovém centru pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="12e13-171">Copy and paste the contents of the database script that creates the Student database, as described in the [Entity Framework documentation](http://msdn.microsoft.com/data/JJ614587.aspx) in the Data Developer Center.</span></span>
<br />

3. <span data-ttu-id="12e13-172">Výběr tlačítka panelu nástrojů symbolem trojúhelníček nebo výběrem položky klíče kombinace kláves Ctrl + Q spusťte skript SQL.</span><span class="sxs-lookup"><span data-stu-id="12e13-172">Run the SQL script by choosing the toolbar button with the triangle symbol or choosing the Ctrl+Q keys.</span></span>
<br />

4. <span data-ttu-id="12e13-173">V **Průzkumníka serveru**, otevřete místní nabídku pro **připojení dat**, zvolte **přidat připojení**a potom zadejte název databázového serveru, název název instance a školní databáze.</span><span class="sxs-lookup"><span data-stu-id="12e13-173">In **Server Explorer**, open the shortcut menu for **Data Connections**, choose **Add Connection**, and then enter the name of the database server, the name of the instance name, and the School database.</span></span>
<br />

5. <span data-ttu-id="12e13-174">Vytvoření projektu jazyka C# nebo Visual Basic konzolovou aplikaci, otevřete jeho místní nabídky, zvolte **přidat novou položku**a potom zvolte **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="12e13-174">Create a C# or Visual Basic Console Application project, open its shortcut menu, choose **Add New Item**, and then choose **ADO.NET Entity Data Model**.</span></span>
<br />  <span data-ttu-id="12e13-175">Spustí se Průvodce datovým modelem entity.</span><span class="sxs-lookup"><span data-stu-id="12e13-175">The Entity Data Model Wizard opens.</span></span> <span data-ttu-id="12e13-176">Pomocí tohoto průvodce můžete zvolit způsob vytvoření datového modelu entity.</span><span class="sxs-lookup"><span data-stu-id="12e13-176">By using this wizard, you can choose how you want to create the Entity Data Model.</span></span>
<br />

6. <span data-ttu-id="12e13-177">V části **zvolte obsah modelu**, vyberte **generování z databáze** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="12e13-177">Under **Choose Model Contents**, select the **Generate from database** check box.</span></span>
<br />

7. <span data-ttu-id="12e13-178">Na další stránce vyberte jako datové připojení nově vytvořenou databázi School.</span><span class="sxs-lookup"><span data-stu-id="12e13-178">On the next page, choose your newly created School database as the data connection.</span></span>
<br />  <span data-ttu-id="12e13-179">Toto připojení by měla vypadat přibližně  **&lt;servername&gt;.&lt; INSTANCENAME&gt;. School.dbo**.</span><span class="sxs-lookup"><span data-stu-id="12e13-179">This connection should resemble **&lt;servername&gt;.&lt;instancename&gt;.School.dbo**.</span></span>
<br />

8. <span data-ttu-id="12e13-180">Zkopírujte připojovací řetězec entity do schránky, protože tento řetězec můžete později potřebovat.</span><span class="sxs-lookup"><span data-stu-id="12e13-180">Copy your entity connection string to the Clipboard because that string might be important later.</span></span>
<br />

9. <span data-ttu-id="12e13-181">Ujistěte se, zaškrtněte políčko pro uložení připojovací řetězec entity k **App.Config** je vybrán soubor a poznamenejte si hodnotu řetězce do textového pole, které by vám pomůžou najít připojovací řetězec později, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="12e13-181">Make sure the check box to save the entity connection string to the **App.Config** file is selected, and make note of the string value in the text box, which should help you locate the connection string later, if needed.</span></span>
<br />

10. <span data-ttu-id="12e13-182">Na další stránce, zvolte **tabulky** a **uložené procedury a funkce**.</span><span class="sxs-lookup"><span data-stu-id="12e13-182">On the next page, choose **Tables** and **Stored Procedures and Functions**.</span></span>
<br />  <span data-ttu-id="12e13-183">Pokud vyberete tyto uzly nejvyšší úrovně, zvolíte také všechny tabulky, uložené procedury a funkce.</span><span class="sxs-lookup"><span data-stu-id="12e13-183">By choosing these top-level nodes, you choose all tables, stored procedures, and functions.</span></span> <span data-ttu-id="12e13-184">V případě potřeby je můžete zvolit také jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="12e13-184">You can also choose these individually, if you want.</span></span>
<br />

11. <span data-ttu-id="12e13-185">Ověřte, zda jste zvolili zaškrtávací políčka i pro ostatní nastavení.</span><span class="sxs-lookup"><span data-stu-id="12e13-185">Make sure that the check boxes for the other settings are selected.</span></span>
<br />  <span data-ttu-id="12e13-186">První **množně nebo singularizovat generované názvy objektů** políčko označuje, zda se ke změně singulární forms množném čísle tak, aby odpovídaly názvů v názvy objektů, které představují databázových tabulek.</span><span class="sxs-lookup"><span data-stu-id="12e13-186">The first **Pluralize or singularize generated object names** check box indicates whether to change singular forms to plural to match conventions in naming objects that represent database tables.</span></span> <span data-ttu-id="12e13-187">**Zahrnout do modelu sloupce cizích klíčů** políčko určuje, zda pro zahrnutí polí, jejichž účelem je připojení k další pole v typy objektů, které jsou generovány pro schéma databáze.</span><span class="sxs-lookup"><span data-stu-id="12e13-187">The **Include foreign key columns in the model** check box determines whether to include fields for which the purpose is to join to other fields in the object types that are generated for the database schema.</span></span> <span data-ttu-id="12e13-188">Třetí zaškrtávací políčko určuje, zda mají být do modelu zahrnuty uložené procedury a funkce.</span><span class="sxs-lookup"><span data-stu-id="12e13-188">The third check box indicates whether to include stored procedures and functions in the model.</span></span>
<br />

12. <span data-ttu-id="12e13-189">Vyberte **Dokončit** pro vygenerování souboru .edmx, který obsahuje datový Model Entity, založený na databázi školy.</span><span class="sxs-lookup"><span data-stu-id="12e13-189">Select the **Finish** button to generate an .edmx file that contains an Entity Data Model that's based on the School database.</span></span>
<br />  <span data-ttu-id="12e13-190">Soubor, **Model1.edmx**, se přidá do projektu, a zobrazí se diagramu databáze.</span><span class="sxs-lookup"><span data-stu-id="12e13-190">A file, **Model1.edmx**, is added to your project, and a database diagram appears.</span></span>
<br />

13. <span data-ttu-id="12e13-191">Na řádku nabídek zvolte **zobrazení**, **ostatní okna**, **Entity Data Model prohlížeče** zobrazíte všechny podrobnosti modelu nebo **podrobnosti mapování Entity Data Model**  otevřete okno, které ukazuje, jak mapuje generovaného objektový model do databáze tabulky a sloupce.</span><span class="sxs-lookup"><span data-stu-id="12e13-191">On the menu bar, choose **View**, **Other Windows**, **Entity Data Model Browser** to view all the details of the model or **Entity Data Model Mapping Details** to open a window that shows how the generated object model maps onto database tables and columns.</span></span>
<br />


## <a name="next-steps"></a><span data-ttu-id="12e13-192">Další kroky</span><span class="sxs-lookup"><span data-stu-id="12e13-192">Next Steps</span></span>
<span data-ttu-id="12e13-193">Prozkoumejte jiné dotazy prohlížením operátory k dispozici dotazu uvedené v [výrazy dotazů](../../language-reference/query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="12e13-193">Explore other queries by looking at the available query operators as listed in [Query Expressions](../../language-reference/query-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="12e13-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="12e13-194">See Also</span></span>
[<span data-ttu-id="12e13-195">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="12e13-195">Type Providers</span></span>](index.md)

[<span data-ttu-id="12e13-196">Edmxfile – zprostředkovatel typu</span><span class="sxs-lookup"><span data-stu-id="12e13-196">EdmxFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="12e13-197">Návod: Přístup k databázi SQL s použitím zprostředkovatelů typů a entit</span><span class="sxs-lookup"><span data-stu-id="12e13-197">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>](accessing-a-sql-database-entities.md)

[<span data-ttu-id="12e13-198">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="12e13-198">Entity Framework</span></span>](http://msdn.microsoft.com/data/ef)

[<span data-ttu-id="12e13-199">Přehled souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="12e13-199">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[<span data-ttu-id="12e13-200">Generátor EDM &#40; EdmGen.exe &#41;</span><span class="sxs-lookup"><span data-stu-id="12e13-200">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)

