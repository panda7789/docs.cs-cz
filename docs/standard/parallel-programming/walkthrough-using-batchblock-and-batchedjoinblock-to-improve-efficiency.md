---
title: 'Návod: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79bbf33ff1b1e843836aa1b93188970b6a1c8ede
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302973"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="04757-102">Návod: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock</span><span class="sxs-lookup"><span data-stu-id="04757-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="04757-103">Knihovna TPL datového toku poskytuje <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> třídy tak, aby se zobrazí a uložit do vyrovnávací paměti dat z jednoho nebo více zdrojů a poté je šířit data ve vyrovnávací paměti jako jednu kolekci.</span><span class="sxs-lookup"><span data-stu-id="04757-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="04757-104">Tento mechanismus dávkování je užitečný při shromažďování dat z jednoho nebo více zdrojů a následném zpracování více datových prvků v dávce.</span><span class="sxs-lookup"><span data-stu-id="04757-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="04757-105">Zvažte například aplikaci, která používá tok dat pro vkládání záznamů do databáze.</span><span class="sxs-lookup"><span data-stu-id="04757-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="04757-106">Tato operace může být efektivnější, pokud je vloženo více položek současně místo postupně sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="04757-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="04757-107">Tento dokument popisuje způsob použití <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> operací vložení třídy ke zvýšení účinnosti takových databáze.</span><span class="sxs-lookup"><span data-stu-id="04757-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="04757-108">Také popisuje způsob použití <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídy pro zachycení výsledků i všech výjimek, ke kterým dochází, když program čte z databáze.</span><span class="sxs-lookup"><span data-stu-id="04757-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="04757-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04757-109">Prerequisites</span></span>  
  
1. <span data-ttu-id="04757-110">Přečtěte si části propojit bloky v [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokument před zahájením tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="04757-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2. <span data-ttu-id="04757-111">Ujistěte se, že máte kopii databáze Northwind, Northwind.sdf, dostupný na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="04757-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="04757-112">Tento soubor je obvykle umístěn ve složce % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span><span class="sxs-lookup"><span data-stu-id="04757-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="04757-113">V některých verzích Windows se nelze připojit k Northwind.sdf Pokud Visual Studio běží v režimu bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="04757-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="04757-114">Pokud chcete připojit k Northwind.sdf, spusťte Visual Studio nebo příkazový řádek vývojáře pro sadu Visual Studio v **spustit jako správce** režimu.</span><span class="sxs-lookup"><span data-stu-id="04757-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="04757-115">Tento návod obsahuje následující části:</span><span class="sxs-lookup"><span data-stu-id="04757-115">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="04757-116">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="04757-116">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="04757-117">Definování třídy zaměstnanců</span><span class="sxs-lookup"><span data-stu-id="04757-117">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="04757-118">Definování operací databáze zaměstnanců</span><span class="sxs-lookup"><span data-stu-id="04757-118">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="04757-119">Přidání dat zaměstnance do databáze bez použití ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="04757-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="04757-120">Použití ukládání do vyrovnávací paměti k přidání dat zaměstnance do databáze</span><span class="sxs-lookup"><span data-stu-id="04757-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="04757-121">Použití spojení ve vyrovnávací paměti pro čtení dat zaměstnanců z databáze</span><span class="sxs-lookup"><span data-stu-id="04757-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="04757-122">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="04757-122">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="04757-123">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="04757-123">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1. <span data-ttu-id="04757-124">V sadě Visual Studio, vytvořit Visual C# nebo Visual Basic **konzolovou aplikaci** projektu.</span><span class="sxs-lookup"><span data-stu-id="04757-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="04757-125">V tomto dokumentu má projekt název `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="04757-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2. <span data-ttu-id="04757-126">Ve vašem projektu přidejte odkaz na System.Data.SqlServerCe.dll a odkaz na System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="04757-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3. <span data-ttu-id="04757-127">Ujistěte se, že Form1.cs (Form1.vb pro jazyk Visual Basic) obsahuje následující `using` (`Imports` v jazyce Visual Basic) příkazy.</span><span class="sxs-lookup"><span data-stu-id="04757-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4. <span data-ttu-id="04757-128">Přidejte následující datové členy do `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="04757-128">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="04757-129">Definování třídy zaměstnanců</span><span class="sxs-lookup"><span data-stu-id="04757-129">Defining the Employee Class</span></span>  
 <span data-ttu-id="04757-130">Přidat `Program` třídy `Employee` třídy.</span><span class="sxs-lookup"><span data-stu-id="04757-130">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="04757-131">`Employee` Třída obsahuje tři vlastnosti `EmployeeID`, `LastName`, a `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="04757-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="04757-132">Tyto vlastnosti odpovídají `Employee ID`, `Last Name`, a `First Name` sloupců `Employees` tabulky v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="04757-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="04757-133">Pro tuto ukázku `Employee` také definuje třídu `Random` metodu, která vytvoří `Employee` objektu s náhodnými hodnotami vlastností.</span><span class="sxs-lookup"><span data-stu-id="04757-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="04757-134">Definování operací databáze zaměstnanců</span><span class="sxs-lookup"><span data-stu-id="04757-134">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="04757-135">Přidat `Program` třídy `InsertEmployees`, `GetEmployeeCount`, a `GetEmployeeID` metody.</span><span class="sxs-lookup"><span data-stu-id="04757-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="04757-136">`InsertEmployees` Metoda přidá nové záznamy zaměstnanců do databáze.</span><span class="sxs-lookup"><span data-stu-id="04757-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="04757-137">`GetEmployeeCount` Metoda zjišťuje počet položek v `Employees` tabulky.</span><span class="sxs-lookup"><span data-stu-id="04757-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="04757-138">`GetEmployeeID` Metoda načte identifikátor prvního zaměstnance, který má zadaný název.</span><span class="sxs-lookup"><span data-stu-id="04757-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="04757-139">Každá z těchto metod má připojovací řetězec k databázi Northwind a používá funkce v `System.Data.SqlServerCe` obor názvů pro komunikaci s databází.</span><span class="sxs-lookup"><span data-stu-id="04757-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="04757-140">Přidání dat zaměstnance do databáze bez použití ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="04757-140">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="04757-141">Přidat `Program` třídy `AddEmployees` a `PostRandomEmployees` metody.</span><span class="sxs-lookup"><span data-stu-id="04757-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="04757-142">`AddEmployees` Metoda přidává náhodná data zaměstnanců do databáze pomocí datového toku.</span><span class="sxs-lookup"><span data-stu-id="04757-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="04757-143">Vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který volá `InsertEmployees` metoda pro přidání položky zaměstnance do databáze.</span><span class="sxs-lookup"><span data-stu-id="04757-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="04757-144">`AddEmployees` Pak zavolá metodu `PostRandomEmployees` metodu ke zveřejnění více `Employee` objektů <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="04757-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="04757-145">`AddEmployees` Metoda pak čeká na dokončení všech operací vložení.</span><span class="sxs-lookup"><span data-stu-id="04757-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="04757-146">Použití ukládání do vyrovnávací paměti k přidání dat zaměstnance do databáze</span><span class="sxs-lookup"><span data-stu-id="04757-146">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="04757-147">Přidat `Program` třídy `AddEmployeesBatched` metody.</span><span class="sxs-lookup"><span data-stu-id="04757-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="04757-148">Tento způsob se podobá `AddEmployees`, s tím rozdílem, že používá také <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídy do vyrovnávací paměti více `Employee` objekty před odesláním těchto objektů do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="04757-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="04757-149">Protože <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídy šíří více prvků jako kolekci, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu je upravit tak, aby mohly reagovat na celou řadu `Employee` objekty.</span><span class="sxs-lookup"><span data-stu-id="04757-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="04757-150">Stejně jako v `AddEmployees` metody `AddEmployeesBatched` volání `PostRandomEmployees` metodu ke zveřejnění více `Employee` objekty; však `AddEmployeesBatched` zveřejní tyto objekty do <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="04757-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="04757-151">`AddEmployeesBatched` Metoda také čeká na dokončení všech operací vložení.</span><span class="sxs-lookup"><span data-stu-id="04757-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="04757-152">Použití spojení ve vyrovnávací paměti pro čtení dat zaměstnanců z databáze</span><span class="sxs-lookup"><span data-stu-id="04757-152">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="04757-153">Přidat `Program` třídy `GetRandomEmployees` metody.</span><span class="sxs-lookup"><span data-stu-id="04757-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="04757-154">Tato metoda vytiskne informace o náhodných zaměstnancích do konzoly.</span><span class="sxs-lookup"><span data-stu-id="04757-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="04757-155">Vytvoří několik náhodných `Employee` a volá `GetEmployeeID` metodu pro načtení jedinečného identifikátoru pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="04757-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="04757-156">Protože `GetEmployeeID` metoda vyvolá výjimku, pokud neexistuje žádný odpovídající zaměstnanec s danou jména a příjmení `GetRandomEmployees` metoda používá <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu pro ukládání `Employee` objekty pro úspěšné volání `GetEmployeeID` a <xref:System.Exception?displayProperty=nameWithType> objekty pro volání, která selžou.</span><span class="sxs-lookup"><span data-stu-id="04757-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="04757-157"><xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt v tomto příkladu zpracovává <xref:System.Tuple%602> objekt, který obsahuje seznam `Employee` objekty a seznam <xref:System.Exception> objekty.</span><span class="sxs-lookup"><span data-stu-id="04757-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="04757-158"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Objekt rozšíří tato data ven při součet přijatého `Employee` a <xref:System.Exception> objekt rovná velikosti dávky.</span><span class="sxs-lookup"><span data-stu-id="04757-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="04757-159">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="04757-159">The Complete Example</span></span>  
 <span data-ttu-id="04757-160">Následující příklad ukazuje kompletní kód.</span><span class="sxs-lookup"><span data-stu-id="04757-160">The following example shows the complete code.</span></span> <span data-ttu-id="04757-161">`Main` Metoda porovnává čas, který se vyžaduje k provedení dávkového vložení do databáze čas k provedení nedávkového vložení do jiné databáze.</span><span class="sxs-lookup"><span data-stu-id="04757-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="04757-162">Ukazuje také použití spojení ve vyrovnávací paměti pro čtení dat zaměstnanců z databáze a také informuje o chybách.</span><span class="sxs-lookup"><span data-stu-id="04757-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="04757-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04757-163">See also</span></span>

- [<span data-ttu-id="04757-164">Tok dat</span><span class="sxs-lookup"><span data-stu-id="04757-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
