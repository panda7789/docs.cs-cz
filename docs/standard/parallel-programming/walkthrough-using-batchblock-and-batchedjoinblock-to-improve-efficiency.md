---
title: "Postupy: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc74b4acc5b29395c05e7c8302caefeb51718282
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="cb9de-102">Postupy: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock</span><span class="sxs-lookup"><span data-stu-id="cb9de-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="cb9de-103">Knihovna toku dat TPL poskytuje <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> třídy, aby mohli přijímat a vyrovnávací paměť dat z jednoho nebo více zdrojů a potom rozšíří na tato data ve vyrovnávací paměti jako jedna kolekce.</span><span class="sxs-lookup"><span data-stu-id="cb9de-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="cb9de-104">Tento mechanismus dávkování je užitečné, když shromažďovat data z jednoho nebo více zdrojů a potom zpracovat více datové prvky, jako dávku.</span><span class="sxs-lookup"><span data-stu-id="cb9de-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="cb9de-105">Představte si třeba aplikaci, která používá toku dat vložení záznamů do databáze.</span><span class="sxs-lookup"><span data-stu-id="cb9de-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="cb9de-106">Tato operace může být efektivnější, pokud jsou ve stejnou dobu namísto postupně postupně vkládána více položek.</span><span class="sxs-lookup"><span data-stu-id="cb9de-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="cb9de-107">Tento dokument popisuje postup použití <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> operace vložení třída zlepšit efektivitu takovou databázi.</span><span class="sxs-lookup"><span data-stu-id="cb9de-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="cb9de-108">Také popisuje způsob použití <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třída zaznamenat výsledky a všechny výjimky, které dojít, když program načte z databáze.</span><span class="sxs-lookup"><span data-stu-id="cb9de-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="cb9de-109">Knihovna toku dat TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> oboru názvů) není distribuované s [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb9de-109">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="cb9de-110">K instalaci <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projektu a vyhledejte online `Microsoft.Tpl.Dataflow` balíčku.</span><span class="sxs-lookup"><span data-stu-id="cb9de-110">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cb9de-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb9de-111">Prerequisites</span></span>  
  
1.  <span data-ttu-id="cb9de-112">Najdete v části připojení bloky [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokumentu před spuštěním tohoto průvodce.</span><span class="sxs-lookup"><span data-stu-id="cb9de-112">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="cb9de-113">Ujistěte se, že máte kopii databáze Northwind, Northwind.sdf v počítači k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cb9de-113">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="cb9de-114">Tento soubor se obvykle nachází ve složce % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span><span class="sxs-lookup"><span data-stu-id="cb9de-114">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="cb9de-115">V některých verzích systému Windows, nemůžete se připojit k Northwind.sdf Pokud [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] běží v režimu bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="cb9de-115">In some versions of Windows, you cannot connect to Northwind.sdf if [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] is running in a non-administrator mode.</span></span> <span data-ttu-id="cb9de-116">Chcete-li se připojit k Northwind.sdf, spusťte [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] nebo [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] příkazového řádku v **spustit jako správce** režimu.</span><span class="sxs-lookup"><span data-stu-id="cb9de-116">To connect to Northwind.sdf, start [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] command prompt in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="cb9de-117">Tento názorný postup obsahuje následující části:</span><span class="sxs-lookup"><span data-stu-id="cb9de-117">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="cb9de-118">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="cb9de-118">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="cb9de-119">Definování zaměstnanec – třída</span><span class="sxs-lookup"><span data-stu-id="cb9de-119">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="cb9de-120">Definování zaměstnanec databázových operací</span><span class="sxs-lookup"><span data-stu-id="cb9de-120">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="cb9de-121">Přidání dat zaměstnanců k databázi bez použití ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="cb9de-121">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="cb9de-122">Chcete-li přidat Data zaměstnanců k databázi pomocí ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="cb9de-122">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="cb9de-123">Použití ve vyrovnávací paměti připojení číst zaměstnanec Data z databáze</span><span class="sxs-lookup"><span data-stu-id="cb9de-123">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="cb9de-124">Úplný příklad</span><span class="sxs-lookup"><span data-stu-id="cb9de-124">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="cb9de-125">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="cb9de-125">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="cb9de-126">V [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vytvořit Visual C# nebo Visual Basic **konzolové aplikace** projektu.</span><span class="sxs-lookup"><span data-stu-id="cb9de-126">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="cb9de-127">V tomto dokumentu je projekt s názvem `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="cb9de-127">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="cb9de-128">Ve vašem projektu přidejte odkaz na System.Data.SqlServerCe.dll a odkaz na System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="cb9de-128">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="cb9de-129">Ujistěte se, že Form1.cs (Form1.vb pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) obsahuje následující `using` (`Imports` v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) příkazy.</span><span class="sxs-lookup"><span data-stu-id="cb9de-129">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="cb9de-130">Přidejte následující členy dat tak, aby `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="cb9de-130">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="cb9de-131">Definování zaměstnanec – třída</span><span class="sxs-lookup"><span data-stu-id="cb9de-131">Defining the Employee Class</span></span>  
 <span data-ttu-id="cb9de-132">Přidejte do `Program` – třída `Employee` třídy.</span><span class="sxs-lookup"><span data-stu-id="cb9de-132">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="cb9de-133">`Employee` Třída obsahuje tři vlastnosti `EmployeeID`, `LastName`, a `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="cb9de-133">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="cb9de-134">Tyto vlastnosti odpovídají `Employee ID`, `Last Name`, a `First Name` sloupců v `Employees` tabulky v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="cb9de-134">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="cb9de-135">Pro tento ukázkový `Employee` třída definuje také `Random` metodu, která vytvoří `Employee` objekt, který má náhodných hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="cb9de-135">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="cb9de-136">Definování zaměstnanec databázových operací</span><span class="sxs-lookup"><span data-stu-id="cb9de-136">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="cb9de-137">Přidejte do `Program` – třída `InsertEmployees`, `GetEmployeeCount`, a `GetEmployeeID` metody.</span><span class="sxs-lookup"><span data-stu-id="cb9de-137">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="cb9de-138">`InsertEmployees` Metoda přidá nové záznamy zaměstnanců k databázi.</span><span class="sxs-lookup"><span data-stu-id="cb9de-138">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="cb9de-139">`GetEmployeeCount` Metoda načte počet položek v `Employees` tabulky.</span><span class="sxs-lookup"><span data-stu-id="cb9de-139">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="cb9de-140">`GetEmployeeID` Metoda načte identifikátor první zaměstnanec, který má zadaný název.</span><span class="sxs-lookup"><span data-stu-id="cb9de-140">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="cb9de-141">Každá z těchto metod přebírá připojovací řetězec k databázi Northwind a používá funkce v `System.Data.SqlServerCe` obor názvů pro komunikaci s databází.</span><span class="sxs-lookup"><span data-stu-id="cb9de-141">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="cb9de-142">Přidání dat zaměstnanců k databázi bez použití ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="cb9de-142">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="cb9de-143">Přidejte do `Program` – třída `AddEmployees` a `PostRandomEmployees` metody.</span><span class="sxs-lookup"><span data-stu-id="cb9de-143">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="cb9de-144">`AddEmployees` Metoda pomocí toku dat přidá náhodných zaměstnanec data do databáze.</span><span class="sxs-lookup"><span data-stu-id="cb9de-144">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="cb9de-145">Vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který volá `InsertEmployees` metody přidat položku zaměstnanců k databázi.</span><span class="sxs-lookup"><span data-stu-id="cb9de-145">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="cb9de-146">`AddEmployees` Metoda pak zavolá `PostRandomEmployees` metodu ke zveřejnění více `Employee` objekty ke <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="cb9de-146">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="cb9de-147">`AddEmployees` Metoda potom počká, než pro všechny operace ukončíte vložení.</span><span class="sxs-lookup"><span data-stu-id="cb9de-147">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="cb9de-148">Chcete-li přidat Data zaměstnanců k databázi pomocí ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="cb9de-148">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="cb9de-149">Přidejte do `Program` – třída `AddEmployeesBatched` metoda.</span><span class="sxs-lookup"><span data-stu-id="cb9de-149">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="cb9de-150">Tato metoda se podobá `AddEmployees`kromě toho, že používá také <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídy mají do vyrovnávací paměti více `Employee` objekty před odesláním těchto objektů do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="cb9de-150">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="cb9de-151">Protože <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třída šíří se víc elementů jako kolekce, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt je upraven tak, aby fungoval na pole `Employee` objekty.</span><span class="sxs-lookup"><span data-stu-id="cb9de-151">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="cb9de-152">Jako v `AddEmployees` metody `AddEmployeesBatched` volání `PostRandomEmployees` metodu ke zveřejnění více `Employee` objekty; však `AddEmployeesBatched` odešle tyto objekty <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="cb9de-152">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="cb9de-153">`AddEmployeesBatched` Metoda čeká také pro všechny operace ukončíte vložení.</span><span class="sxs-lookup"><span data-stu-id="cb9de-153">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="cb9de-154">Použití ve vyrovnávací paměti připojení číst zaměstnanec Data z databáze</span><span class="sxs-lookup"><span data-stu-id="cb9de-154">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="cb9de-155">Přidejte do `Program` – třída `GetRandomEmployees` metoda.</span><span class="sxs-lookup"><span data-stu-id="cb9de-155">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="cb9de-156">Tato metoda zobrazí informace o náhodné zaměstnanci ke konzole.</span><span class="sxs-lookup"><span data-stu-id="cb9de-156">This method prints information about random employees to the console.</span></span> <span data-ttu-id="cb9de-157">Vytvoří několik náhodných `Employee` objekty a volání `GetEmployeeID` metoda pro načtení jedinečný identifikátor pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="cb9de-157">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="cb9de-158">Protože `GetEmployeeID` metoda vyvolá výjimku, pokud neexistuje žádný odpovídající zaměstnanec s danou první a poslední názvy `GetRandomEmployees` metoda používá <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu pro ukládání `Employee` objekty pro úspěšné volání `GetEmployeeID` a <xref:System.Exception?displayProperty=nameWithType> objekty pro volání, které nesplní.</span><span class="sxs-lookup"><span data-stu-id="cb9de-158">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="cb9de-159"><xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt v tomto příkladu funguje na <xref:System.Tuple%602> objekt, který obsahuje seznam `Employee` objekty a seznam <xref:System.Exception> objekty.</span><span class="sxs-lookup"><span data-stu-id="cb9de-159">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="cb9de-160"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Objekt šíří se tato data při součet přijatého `Employee` a <xref:System.Exception> počty objekt rovná velikost dávky.</span><span class="sxs-lookup"><span data-stu-id="cb9de-160">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="cb9de-161">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="cb9de-161">The Complete Example</span></span>  
 <span data-ttu-id="cb9de-162">Následující příklad ukazuje kód dokončení.</span><span class="sxs-lookup"><span data-stu-id="cb9de-162">The following example shows the complete code.</span></span> <span data-ttu-id="cb9de-163">`Main` Metoda srovnává čas, který je potřeba provést vložení dávkové databáze a čas k vložení databáze není v dávce.</span><span class="sxs-lookup"><span data-stu-id="cb9de-163">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="cb9de-164">Také ukazuje použití ve vyrovnávací paměti připojení ke čtení zaměstnanec dat z databáze a také zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="cb9de-164">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="cb9de-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb9de-165">See Also</span></span>  
 [<span data-ttu-id="cb9de-166">Toku dat</span><span class="sxs-lookup"><span data-stu-id="cb9de-166">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
