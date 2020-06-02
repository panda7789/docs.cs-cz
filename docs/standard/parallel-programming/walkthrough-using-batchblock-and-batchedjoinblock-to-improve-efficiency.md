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
ms.openlocfilehash: e572c5a14958ccc069ae7649af8c8ed4eb967dc1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284582"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="e33f5-102">Návod: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock</span><span class="sxs-lookup"><span data-stu-id="e33f5-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>

<span data-ttu-id="e33f5-103">Knihovna rozhraní TPL Dataflow poskytuje <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> třídy a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> , aby bylo možné přijímat data a ukládat je do vyrovnávací paměti z jednoho nebo více zdrojů a následně šířit tato data do vyrovnávací paměti jako jednu kolekci.</span><span class="sxs-lookup"><span data-stu-id="e33f5-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="e33f5-104">Tento mechanismus dávkování je užitečný při shromažďování dat z jednoho nebo více zdrojů a následném zpracování více datových prvků jako dávky.</span><span class="sxs-lookup"><span data-stu-id="e33f5-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="e33f5-105">Představte si například aplikaci, která používá tok k vkládání záznamů do databáze.</span><span class="sxs-lookup"><span data-stu-id="e33f5-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="e33f5-106">Tato operace může být efektivnější, pokud je vloženo více položek současně namísto jednoho intervalu.</span><span class="sxs-lookup"><span data-stu-id="e33f5-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="e33f5-107">Tento dokument popisuje, jak použít <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídu ke zlepšení efektivity těchto operací vložení databáze.</span><span class="sxs-lookup"><span data-stu-id="e33f5-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="e33f5-108">Popisuje také, jak použít <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu k zachycení výsledků a všech výjimek, ke kterým dojde, když program čte z databáze.</span><span class="sxs-lookup"><span data-stu-id="e33f5-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="e33f5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e33f5-109">Prerequisites</span></span>

1. <span data-ttu-id="e33f5-110">Než začnete tento návod, přečtěte si část bloky spojení v dokumentu [toku](dataflow-task-parallel-library.md) dat.</span><span class="sxs-lookup"><span data-stu-id="e33f5-110">Read the Join Blocks section in the [Dataflow](dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>

2. <span data-ttu-id="e33f5-111">Ujistěte se, že máte kopii databáze Northwind, Northwind. SDF, která je k dispozici ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="e33f5-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="e33f5-112">Tento soubor je obvykle umístěn ve složce% Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples \\ .</span><span class="sxs-lookup"><span data-stu-id="e33f5-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e33f5-113">V některých verzích systému Windows se nelze připojit k databázi Northwind. SDF, pokud je aplikace Visual Studio spuštěna v režimu bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="e33f5-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="e33f5-114">Pokud se chcete připojit k Northwind. SDF, spusťte aplikaci Visual Studio nebo Developer Command Prompt pro Visual Studio v režimu **Spustit jako správce** .</span><span class="sxs-lookup"><span data-stu-id="e33f5-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>

<span data-ttu-id="e33f5-115">Tento návod obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="e33f5-115">This walkthrough contains the following sections:</span></span>

- [<span data-ttu-id="e33f5-116">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="e33f5-116">Creating the Console Application</span></span>](#creating)

- [<span data-ttu-id="e33f5-117">Definování třídy Employee</span><span class="sxs-lookup"><span data-stu-id="e33f5-117">Defining the Employee Class</span></span>](#employeeClass)

- [<span data-ttu-id="e33f5-118">Definování operací databáze zaměstnanců</span><span class="sxs-lookup"><span data-stu-id="e33f5-118">Defining Employee Database Operations</span></span>](#operations)

- [<span data-ttu-id="e33f5-119">Přidání dat zaměstnanců do databáze bez použití ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="e33f5-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)

- [<span data-ttu-id="e33f5-120">Přidání dat zaměstnanců do databáze pomocí ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="e33f5-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)

- [<span data-ttu-id="e33f5-121">Čtení dat zaměstnanců z databáze pomocí připojení do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="e33f5-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)

- [<span data-ttu-id="e33f5-122">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="e33f5-122">The Complete Example</span></span>](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a><span data-ttu-id="e33f5-123">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="e33f5-123">Creating the Console Application</span></span>

1. <span data-ttu-id="e33f5-124">V aplikaci Visual Studio vytvořte projekt **konzolové aplikace** Visual C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e33f5-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="e33f5-125">V tomto dokumentu se projekt jmenuje `DataflowBatchDatabase` .</span><span class="sxs-lookup"><span data-stu-id="e33f5-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>

2. <span data-ttu-id="e33f5-126">V projektu přidejte odkaz na System. data. SqlServerCe. dll a odkaz na System. Threading. Tasks. Dataflow. dll.</span><span class="sxs-lookup"><span data-stu-id="e33f5-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>

3. <span data-ttu-id="e33f5-127">Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje `using` následující `Imports` příkazy (v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e33f5-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. <span data-ttu-id="e33f5-128">Přidejte do třídy následující datové členy `Program` .</span><span class="sxs-lookup"><span data-stu-id="e33f5-128">Add the following data members to the `Program` class.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a><span data-ttu-id="e33f5-129">Definování třídy Employee</span><span class="sxs-lookup"><span data-stu-id="e33f5-129">Defining the Employee Class</span></span>

<span data-ttu-id="e33f5-130">Přidejte do `Program` třídy třídu `Employee` .</span><span class="sxs-lookup"><span data-stu-id="e33f5-130">Add to the `Program` class the `Employee` class.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

<span data-ttu-id="e33f5-131">`Employee`Třída obsahuje tři vlastnosti,, `EmployeeID` `LastName` a `FirstName` .</span><span class="sxs-lookup"><span data-stu-id="e33f5-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="e33f5-132">Tyto vlastnosti odpovídají `Employee ID` `Last Name` `First Name` sloupcům, a v `Employees` tabulce databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="e33f5-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="e33f5-133">Pro tuto ukázku `Employee` Třída také definuje `Random` metodu, která vytvoří `Employee` objekt, který má náhodné hodnoty pro jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e33f5-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a><span data-ttu-id="e33f5-134">Definování operací databáze zaměstnanců</span><span class="sxs-lookup"><span data-stu-id="e33f5-134">Defining Employee Database Operations</span></span>

<span data-ttu-id="e33f5-135">Přidejte do `Program` třídy `InsertEmployees` `GetEmployeeCount` metody, a `GetEmployeeID` .</span><span class="sxs-lookup"><span data-stu-id="e33f5-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

<span data-ttu-id="e33f5-136">`InsertEmployees`Metoda přidá do databáze nové záznamy o zaměstnancích.</span><span class="sxs-lookup"><span data-stu-id="e33f5-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="e33f5-137">`GetEmployeeCount`Metoda načte počet položek v `Employees` tabulce.</span><span class="sxs-lookup"><span data-stu-id="e33f5-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="e33f5-138">`GetEmployeeID`Metoda načte identifikátor prvního zaměstnance, který má zadaný název.</span><span class="sxs-lookup"><span data-stu-id="e33f5-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="e33f5-139">Každá z těchto metod vezme připojovací řetězec k databázi Northwind a používá funkce v `System.Data.SqlServerCe` oboru názvů ke komunikaci s databází.</span><span class="sxs-lookup"><span data-stu-id="e33f5-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="e33f5-140">Přidání dat zaměstnanců do databáze bez použití ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="e33f5-140">Adding Employee Data to the Database Without Using Buffering</span></span>

<span data-ttu-id="e33f5-141">Přidejte do `Program` třídy `AddEmployees` `PostRandomEmployees` metody a.</span><span class="sxs-lookup"><span data-stu-id="e33f5-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

<span data-ttu-id="e33f5-142">`AddEmployees`Metoda přidá náhodná data zaměstnanců do databáze pomocí toku dat.</span><span class="sxs-lookup"><span data-stu-id="e33f5-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="e33f5-143">Vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který volá `InsertEmployees` metodu pro přidání záznamu zaměstnance do databáze.</span><span class="sxs-lookup"><span data-stu-id="e33f5-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="e33f5-144">`AddEmployees`Metoda pak zavolá `PostRandomEmployees` metodu pro odeslání více `Employee` objektů do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="e33f5-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="e33f5-145">`AddEmployees`Metoda pak počká na dokončení všech operací vložení.</span><span class="sxs-lookup"><span data-stu-id="e33f5-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="e33f5-146">Přidání dat zaměstnanců do databáze pomocí ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="e33f5-146">Using Buffering to Add Employee Data to the Database</span></span>

<span data-ttu-id="e33f5-147">Přidejte do `Program` třídy `AddEmployeesBatched` metodu.</span><span class="sxs-lookup"><span data-stu-id="e33f5-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

<span data-ttu-id="e33f5-148">Tato metoda se podobá `AddEmployees` , s tím rozdílem, že také používá <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> třídu k ukládání více objektů do vyrovnávací paměti `Employee` předtím, než je pošle tyto objekty <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="e33f5-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="e33f5-149">Vzhledem k tomu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> , že třída šíří více prvků jako kolekci, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt je upraven tak, aby fungoval na poli `Employee` objektů.</span><span class="sxs-lookup"><span data-stu-id="e33f5-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="e33f5-150">Stejně jako v `AddEmployees` metodě `AddEmployeesBatched` volá `PostRandomEmployees` metodu pro odeslání více `Employee` objektů; `AddEmployeesBatched` tyto objekty však tyto objekty odešle do <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="e33f5-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="e33f5-151">`AddEmployeesBatched`Metoda také čeká na dokončení všech operací vložení.</span><span class="sxs-lookup"><span data-stu-id="e33f5-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="e33f5-152">Čtení dat zaměstnanců z databáze pomocí připojení do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="e33f5-152">Using Buffered Join to Read Employee Data from the Database</span></span>

<span data-ttu-id="e33f5-153">Přidejte do `Program` třídy `GetRandomEmployees` metodu.</span><span class="sxs-lookup"><span data-stu-id="e33f5-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

<span data-ttu-id="e33f5-154">Tato metoda vytiskne informace o náhodných zaměstnancích do konzoly.</span><span class="sxs-lookup"><span data-stu-id="e33f5-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="e33f5-155">Vytvoří několik náhodných `Employee` objektů a zavolá `GetEmployeeID` metodu pro načtení jedinečného identifikátoru pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="e33f5-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="e33f5-156">Vzhledem k tomu, že `GetEmployeeID` metoda vyvolá výjimku, pokud neexistuje žádný odpovídající zaměstnanec s danými křestními a posledními názvy, `GetRandomEmployees` Metoda používá <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu k ukládání `Employee` objektů pro úspěšná volání `GetEmployeeID` a <xref:System.Exception?displayProperty=nameWithType> objekty pro volání, která selžou.</span><span class="sxs-lookup"><span data-stu-id="e33f5-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="e33f5-157"><xref:System.Threading.Tasks.Dataflow.ActionBlock%601>Objekt v tomto příkladu funguje na <xref:System.Tuple%602> objektu, který obsahuje seznam `Employee` objektů a seznam <xref:System.Exception> objektů.</span><span class="sxs-lookup"><span data-stu-id="e33f5-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="e33f5-158"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>Objekt šíří tato data v případě, že součet přijatých hodnot `Employee` a <xref:System.Exception> počtu objektů se rovná velikosti dávky.</span><span class="sxs-lookup"><span data-stu-id="e33f5-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>

<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="e33f5-159">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="e33f5-159">The Complete Example</span></span>

<span data-ttu-id="e33f5-160">Následující příklad ukazuje úplný kód.</span><span class="sxs-lookup"><span data-stu-id="e33f5-160">The following example shows the complete code.</span></span> <span data-ttu-id="e33f5-161">`Main`Metoda porovnává dobu potřebnou k provedení vkládání dávkových databází oproti době provádění nedávkových vkládání databází.</span><span class="sxs-lookup"><span data-stu-id="e33f5-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="e33f5-162">Ukazuje také použití spojení ve vyrovnávací paměti pro čtení dat zaměstnanců z databáze a také hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="e33f5-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a><span data-ttu-id="e33f5-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="e33f5-163">See also</span></span>

- [<span data-ttu-id="e33f5-164">Tok dat</span><span class="sxs-lookup"><span data-stu-id="e33f5-164">Dataflow</span></span>](dataflow-task-parallel-library.md)
