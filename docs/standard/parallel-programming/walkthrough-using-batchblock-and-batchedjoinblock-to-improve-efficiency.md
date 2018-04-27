---
title: 'Postupy: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c9ea53fb186551a24f678d905d35caaaa0c26494
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="82b7a-102">Postupy: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock</span><span class="sxs-lookup"><span data-stu-id="82b7a-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="82b7a-103">Knihovna toku dat TPL poskytuje <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> třídy, aby mohli přijímat a vyrovnávací paměť dat z jednoho nebo více zdrojů a potom rozšíří na tato data ve vyrovnávací paměti jako jedna kolekce.</span><span class="sxs-lookup"><span data-stu-id="82b7a-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="82b7a-104">Tento mechanismus dávkování je užitečné, když shromažďovat data z jednoho nebo více zdrojů a potom zpracovat více datové prvky, jako dávku.</span><span class="sxs-lookup"><span data-stu-id="82b7a-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="82b7a-105">Představte si třeba aplikaci, která používá toku dat vložení záznamů do databáze.</span><span class="sxs-lookup"><span data-stu-id="82b7a-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="82b7a-106">Tato operace může být efektivnější, pokud jsou ve stejnou dobu namísto postupně postupně vkládána více položek.</span><span class="sxs-lookup"><span data-stu-id="82b7a-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="82b7a-107">Tento dokument popisuje postup použití <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> operace vložení třída zlepšit efektivitu takovou databázi.</span><span class="sxs-lookup"><span data-stu-id="82b7a-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="82b7a-108">Také popisuje způsob použití <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třída zaznamenat výsledky a všechny výjimky, které dojít, když program načte z databáze.</span><span class="sxs-lookup"><span data-stu-id="82b7a-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="82b7a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82b7a-109">Prerequisites</span></span>  
  
1.  <span data-ttu-id="82b7a-110">Najdete v části připojení bloky [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokumentu před spuštěním tohoto průvodce.</span><span class="sxs-lookup"><span data-stu-id="82b7a-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="82b7a-111">Ujistěte se, že máte kopii databáze Northwind, Northwind.sdf v počítači k dispozici.</span><span class="sxs-lookup"><span data-stu-id="82b7a-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="82b7a-112">Tento soubor se obvykle nachází ve složce % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span><span class="sxs-lookup"><span data-stu-id="82b7a-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="82b7a-113">V některých verzích systému Windows, nemůžete se připojit k Northwind.sdf Pokud [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] běží v režimu bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="82b7a-113">In some versions of Windows, you cannot connect to Northwind.sdf if [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] is running in a non-administrator mode.</span></span> <span data-ttu-id="82b7a-114">Chcete-li se připojit k Northwind.sdf, spusťte [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] nebo [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] příkazového řádku v **spustit jako správce** režimu.</span><span class="sxs-lookup"><span data-stu-id="82b7a-114">To connect to Northwind.sdf, start [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] command prompt in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="82b7a-115">Tento názorný postup obsahuje následující části:</span><span class="sxs-lookup"><span data-stu-id="82b7a-115">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="82b7a-116">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="82b7a-116">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="82b7a-117">Definování zaměstnanec – třída</span><span class="sxs-lookup"><span data-stu-id="82b7a-117">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="82b7a-118">Definování zaměstnanec databázových operací</span><span class="sxs-lookup"><span data-stu-id="82b7a-118">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="82b7a-119">Přidání dat zaměstnanců k databázi bez použití ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="82b7a-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="82b7a-120">Chcete-li přidat Data zaměstnanců k databázi pomocí ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="82b7a-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="82b7a-121">Použití ve vyrovnávací paměti připojení číst zaměstnanec Data z databáze</span><span class="sxs-lookup"><span data-stu-id="82b7a-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="82b7a-122">Úplný příklad</span><span class="sxs-lookup"><span data-stu-id="82b7a-122">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="82b7a-123">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="82b7a-123">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="82b7a-124">V [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vytvořit Visual C# nebo Visual Basic **konzolové aplikace** projektu.</span><span class="sxs-lookup"><span data-stu-id="82b7a-124">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="82b7a-125">V tomto dokumentu je projekt s názvem `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="82b7a-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="82b7a-126">Ve vašem projektu přidejte odkaz na System.Data.SqlServerCe.dll a odkaz na System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="82b7a-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="82b7a-127">Ujistěte se, že Form1.cs (Form1.vb jazyka Visual Basic) obsahuje následující `using` (`Imports` v jazyce Visual Basic) příkazy.</span><span class="sxs-lookup"><span data-stu-id="82b7a-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="82b7a-128">Přidejte následující členy dat tak, aby `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="82b7a-128">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="82b7a-129">Definování zaměstnanec – třída</span><span class="sxs-lookup"><span data-stu-id="82b7a-129">Defining the Employee Class</span></span>  
 <span data-ttu-id="82b7a-130">Přidejte do `Program` – třída `Employee` třídy.</span><span class="sxs-lookup"><span data-stu-id="82b7a-130">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="82b7a-131">`Employee` Třída obsahuje tři vlastnosti `EmployeeID`, `LastName`, a `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="82b7a-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="82b7a-132">Tyto vlastnosti odpovídají `Employee ID`, `Last Name`, a `First Name` sloupců v `Employees` tabulky v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="82b7a-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="82b7a-133">Pro tento ukázkový `Employee` třída definuje také `Random` metodu, která vytvoří `Employee` objekt, který má náhodných hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="82b7a-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="82b7a-134">Definování zaměstnanec databázových operací</span><span class="sxs-lookup"><span data-stu-id="82b7a-134">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="82b7a-135">Přidejte do `Program` – třída `InsertEmployees`, `GetEmployeeCount`, a `GetEmployeeID` metody.</span><span class="sxs-lookup"><span data-stu-id="82b7a-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="82b7a-136">`InsertEmployees` Metoda přidá nové záznamy zaměstnanců k databázi.</span><span class="sxs-lookup"><span data-stu-id="82b7a-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="82b7a-137">`GetEmployeeCount` Metoda načte počet položek v `Employees` tabulky.</span><span class="sxs-lookup"><span data-stu-id="82b7a-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="82b7a-138">`GetEmployeeID` Metoda načte identifikátor první zaměstnanec, který má zadaný název.</span><span class="sxs-lookup"><span data-stu-id="82b7a-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="82b7a-139">Každá z těchto metod přebírá připojovací řetězec k databázi Northwind a používá funkce v `System.Data.SqlServerCe` obor názvů pro komunikaci s databází.</span><span class="sxs-lookup"><span data-stu-id="82b7a-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="82b7a-140">Přidání dat zaměstnanců k databázi bez použití ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="82b7a-140">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="82b7a-141">Přidejte do `Program` – třída `AddEmployees` a `PostRandomEmployees` metody.</span><span class="sxs-lookup"><span data-stu-id="82b7a-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="82b7a-142">`AddEmployees` Metoda pomocí toku dat přidá náhodných zaměstnanec data do databáze.</span><span class="sxs-lookup"><span data-stu-id="82b7a-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="82b7a-143">Vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který volá `InsertEmployees` metody přidat položku zaměstnanců k databázi.</span><span class="sxs-lookup"><span data-stu-id="82b7a-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="82b7a-144">`AddEmployees` Metoda pak zavolá `PostRandomEmployees` metodu ke zveřejnění více `Employee` objekty ke <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="82b7a-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="82b7a-145">`AddEmployees` Metoda potom počká, než pro všechny operace ukončíte vložení.</span><span class="sxs-lookup"><span data-stu-id="82b7a-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="82b7a-146">Chcete-li přidat Data zaměstnanců k databázi pomocí ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="82b7a-146">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="82b7a-147">Přidejte do `Program` – třída `AddEmployeesBatched` metoda.</span><span class="sxs-lookup"><span data-stu-id="82b7a-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="82b7a-148">Tato metoda se podobá `AddEmployees`kromě toho, že používá také <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídy mají do vyrovnávací paměti více `Employee` objekty před odesláním těchto objektů do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="82b7a-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="82b7a-149">Protože <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třída šíří se víc elementů jako kolekce, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt je upraven tak, aby fungoval na pole `Employee` objekty.</span><span class="sxs-lookup"><span data-stu-id="82b7a-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="82b7a-150">Jako v `AddEmployees` metody `AddEmployeesBatched` volání `PostRandomEmployees` metodu ke zveřejnění více `Employee` objekty; však `AddEmployeesBatched` odešle tyto objekty <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="82b7a-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="82b7a-151">`AddEmployeesBatched` Metoda čeká také pro všechny operace ukončíte vložení.</span><span class="sxs-lookup"><span data-stu-id="82b7a-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="82b7a-152">Použití ve vyrovnávací paměti připojení číst zaměstnanec Data z databáze</span><span class="sxs-lookup"><span data-stu-id="82b7a-152">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="82b7a-153">Přidejte do `Program` – třída `GetRandomEmployees` metoda.</span><span class="sxs-lookup"><span data-stu-id="82b7a-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="82b7a-154">Tato metoda zobrazí informace o náhodné zaměstnanci ke konzole.</span><span class="sxs-lookup"><span data-stu-id="82b7a-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="82b7a-155">Vytvoří několik náhodných `Employee` objekty a volání `GetEmployeeID` metoda pro načtení jedinečný identifikátor pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="82b7a-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="82b7a-156">Protože `GetEmployeeID` metoda vyvolá výjimku, pokud neexistuje žádný odpovídající zaměstnanec s danou první a poslední názvy `GetRandomEmployees` metoda používá <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu pro ukládání `Employee` objekty pro úspěšné volání `GetEmployeeID` a <xref:System.Exception?displayProperty=nameWithType> objekty pro volání, které nesplní.</span><span class="sxs-lookup"><span data-stu-id="82b7a-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="82b7a-157"><xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt v tomto příkladu funguje na <xref:System.Tuple%602> objekt, který obsahuje seznam `Employee` objekty a seznam <xref:System.Exception> objekty.</span><span class="sxs-lookup"><span data-stu-id="82b7a-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="82b7a-158"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Objekt šíří se tato data při součet přijatého `Employee` a <xref:System.Exception> počty objekt rovná velikost dávky.</span><span class="sxs-lookup"><span data-stu-id="82b7a-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="82b7a-159">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="82b7a-159">The Complete Example</span></span>  
 <span data-ttu-id="82b7a-160">Následující příklad ukazuje kód dokončení.</span><span class="sxs-lookup"><span data-stu-id="82b7a-160">The following example shows the complete code.</span></span> <span data-ttu-id="82b7a-161">`Main` Metoda srovnává čas, který je potřeba provést vložení dávkové databáze a čas k vložení databáze není v dávce.</span><span class="sxs-lookup"><span data-stu-id="82b7a-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="82b7a-162">Také ukazuje použití ve vyrovnávací paměti připojení ke čtení zaměstnanec dat z databáze a také zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="82b7a-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="82b7a-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="82b7a-163">See Also</span></span>  
 [<span data-ttu-id="82b7a-164">Tok dat</span><span class="sxs-lookup"><span data-stu-id="82b7a-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
