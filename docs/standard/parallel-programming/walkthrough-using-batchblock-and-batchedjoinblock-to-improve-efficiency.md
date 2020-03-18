---
title: 'Postupy: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
ms.openlocfilehash: 4b2b6a6124bf8cc0fb3b379607135283678e3268
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091363"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="7cb25-102">Postupy: Zvýšení efektivity díky použití tříd BatchBlock a BatchedJoinBlock</span><span class="sxs-lookup"><span data-stu-id="7cb25-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>

<span data-ttu-id="7cb25-103">Knihovna toku dat <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> TPL poskytuje a <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> třídy, takže můžete přijímat a ukládání dat do vyrovnávací paměti z jednoho nebo více zdrojů a potom šířit data ve vyrovnávací paměti jako jednu kolekci.</span><span class="sxs-lookup"><span data-stu-id="7cb25-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="7cb25-104">Tento mechanismus dávkování je užitečné při shromažďování dat z jednoho nebo více zdrojů a potom zpracovat více datových prvků jako dávka.</span><span class="sxs-lookup"><span data-stu-id="7cb25-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="7cb25-105">Zvažte například aplikaci, která používá tok dat k vložení záznamů do databáze.</span><span class="sxs-lookup"><span data-stu-id="7cb25-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="7cb25-106">Tato operace může být efektivnější, pokud více položek jsou vloženy současně namísto jednoho po druhém postupně.</span><span class="sxs-lookup"><span data-stu-id="7cb25-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="7cb25-107">Tento dokument popisuje, jak <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> použít třídu ke zlepšení efektivity těchto operací vkládání databáze.</span><span class="sxs-lookup"><span data-stu-id="7cb25-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="7cb25-108">Popisuje také, jak použít <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> třídu k zachycení výsledků a všech výjimek, ke kterým dochází při čtení programu z databáze.</span><span class="sxs-lookup"><span data-stu-id="7cb25-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="7cb25-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7cb25-109">Prerequisites</span></span>

1. <span data-ttu-id="7cb25-110">Než začnete s tímto návodem, přečtěte si oddíl Bloky spojení v dokumentu [Tok dat.](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)</span><span class="sxs-lookup"><span data-stu-id="7cb25-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>

2. <span data-ttu-id="7cb25-111">Ujistěte se, že máte v počítači k dispozici kopii databáze Northwind, Northwind.sdf.</span><span class="sxs-lookup"><span data-stu-id="7cb25-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="7cb25-112">Tento soubor je obvykle umístěn ve složce %Program Files%\Microsoft SQL Server\\Compact Edition\v3.5\Samples .</span><span class="sxs-lookup"><span data-stu-id="7cb25-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7cb25-113">V některých verzích systému Windows se nelze připojit k souboru Northwind.sdf, pokud je sada Visual Studio spuštěna v režimu bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="7cb25-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="7cb25-114">Chcete-li se připojit k souboru Northwind.sdf, spusťte visual studio nebo příkazový řádek pro vývojáře pro Visual Studio v režimu **Spustit jako správce.**</span><span class="sxs-lookup"><span data-stu-id="7cb25-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>

<span data-ttu-id="7cb25-115">Tento návod obsahuje následující části:</span><span class="sxs-lookup"><span data-stu-id="7cb25-115">This walkthrough contains the following sections:</span></span>

- [<span data-ttu-id="7cb25-116">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="7cb25-116">Creating the Console Application</span></span>](#creating)

- [<span data-ttu-id="7cb25-117">Definování třídy zaměstnanců</span><span class="sxs-lookup"><span data-stu-id="7cb25-117">Defining the Employee Class</span></span>](#employeeClass)

- [<span data-ttu-id="7cb25-118">Definování operací databáze zaměstnanců</span><span class="sxs-lookup"><span data-stu-id="7cb25-118">Defining Employee Database Operations</span></span>](#operations)

- [<span data-ttu-id="7cb25-119">Přidání dat zaměstnance do databáze bez použití ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="7cb25-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)

- [<span data-ttu-id="7cb25-120">Použití ukládání do vyrovnávací paměti k přidání dat zaměstnance do databáze</span><span class="sxs-lookup"><span data-stu-id="7cb25-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)

- [<span data-ttu-id="7cb25-121">Použití spojení ve vyrovnávací paměti ke čtení dat zaměstnanců z databáze</span><span class="sxs-lookup"><span data-stu-id="7cb25-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)

- [<span data-ttu-id="7cb25-122">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="7cb25-122">The Complete Example</span></span>](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a><span data-ttu-id="7cb25-123">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="7cb25-123">Creating the Console Application</span></span>

1. <span data-ttu-id="7cb25-124">V sadě Visual Studio vytvořte projekt aplikace Visual C# nebo Visual Basic **Console.**</span><span class="sxs-lookup"><span data-stu-id="7cb25-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="7cb25-125">V tomto dokumentu je `DataflowBatchDatabase`projekt pojmenován .</span><span class="sxs-lookup"><span data-stu-id="7cb25-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>

2. <span data-ttu-id="7cb25-126">V projektu přidejte odkaz na soubor System.Data.SqlServerCe.dll a odkaz na soubor System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="7cb25-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>

3. <span data-ttu-id="7cb25-127">Ujistěte se, že Form1.cs (Form1.vb `using` `Imports` pro visual basic) obsahuje následující příkazy ( v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7cb25-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. <span data-ttu-id="7cb25-128">Přidejte následující datové `Program` členy do třídy.</span><span class="sxs-lookup"><span data-stu-id="7cb25-128">Add the following data members to the `Program` class.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a><span data-ttu-id="7cb25-129">Definování třídy zaměstnanců</span><span class="sxs-lookup"><span data-stu-id="7cb25-129">Defining the Employee Class</span></span>

<span data-ttu-id="7cb25-130">Přidejte `Program` do `Employee` třídy třídy.</span><span class="sxs-lookup"><span data-stu-id="7cb25-130">Add to the `Program` class the `Employee` class.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

<span data-ttu-id="7cb25-131">Třída `Employee` obsahuje tři `EmployeeID`vlastnosti , `LastName`, a `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="7cb25-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="7cb25-132">Tyto vlastnosti `Employee ID`odpovídají `Last Name`, `First Name` a `Employees` sloupce v tabulce v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="7cb25-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="7cb25-133">Pro tuto demonstraci `Employee` třída také `Random` definuje metodu, která vytvoří `Employee` objekt, který má náhodné hodnoty pro své vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7cb25-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a><span data-ttu-id="7cb25-134">Definování operací databáze zaměstnanců</span><span class="sxs-lookup"><span data-stu-id="7cb25-134">Defining Employee Database Operations</span></span>

<span data-ttu-id="7cb25-135">Přidejte `Program` do `InsertEmployees`třídy `GetEmployeeCount` `GetEmployeeID` , a metody.</span><span class="sxs-lookup"><span data-stu-id="7cb25-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

<span data-ttu-id="7cb25-136">Metoda `InsertEmployees` přidá do databáze nové záznamy zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="7cb25-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="7cb25-137">Metoda `GetEmployeeCount` načte počet položek v `Employees` tabulce.</span><span class="sxs-lookup"><span data-stu-id="7cb25-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="7cb25-138">Metoda `GetEmployeeID` načte identifikátor prvního zaměstnance, který má zadaný název.</span><span class="sxs-lookup"><span data-stu-id="7cb25-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="7cb25-139">Každá z těchto metod přebírá připojovací řetězec do `System.Data.SqlServerCe` databáze Northwind a používá funkce v oboru názvů ke komunikaci s databází.</span><span class="sxs-lookup"><span data-stu-id="7cb25-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="7cb25-140">Přidání dat zaměstnance do databáze bez použití ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="7cb25-140">Adding Employee Data to the Database Without Using Buffering</span></span>

<span data-ttu-id="7cb25-141">Přidejte `Program` do `AddEmployees` třídy a `PostRandomEmployees` metody.</span><span class="sxs-lookup"><span data-stu-id="7cb25-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

<span data-ttu-id="7cb25-142">Metoda `AddEmployees` přidá do databáze náhodná data zaměstnanců pomocí toku dat.</span><span class="sxs-lookup"><span data-stu-id="7cb25-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="7cb25-143">Vytvoří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který `InsertEmployees` volá metodu přidat položku zaměstnance do databáze.</span><span class="sxs-lookup"><span data-stu-id="7cb25-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="7cb25-144">Metoda `AddEmployees` pak volá `PostRandomEmployees` metodu `Employee` zaúčtovat <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> více objektů do objektu.</span><span class="sxs-lookup"><span data-stu-id="7cb25-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="7cb25-145">Metoda `AddEmployees` pak čeká na dokončení všech operací vložení.</span><span class="sxs-lookup"><span data-stu-id="7cb25-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="7cb25-146">Použití ukládání do vyrovnávací paměti k přidání dat zaměstnance do databáze</span><span class="sxs-lookup"><span data-stu-id="7cb25-146">Using Buffering to Add Employee Data to the Database</span></span>

<span data-ttu-id="7cb25-147">Přidejte `Program` do `AddEmployeesBatched` třídy metodu.</span><span class="sxs-lookup"><span data-stu-id="7cb25-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

<span data-ttu-id="7cb25-148">Tato metoda `AddEmployees`se podobá , s <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> tím rozdílem, že také používá třídu do vyrovnávací paměti více `Employee` objektů před odesláním těchto objektů do objektu. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601></span><span class="sxs-lookup"><span data-stu-id="7cb25-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="7cb25-149">Vzhledem <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> k tomu, že třída šíří <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> více prvků jako kolekce, `Employee` objekt je upraven tak, aby působit na pole objektů.</span><span class="sxs-lookup"><span data-stu-id="7cb25-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="7cb25-150">Stejně `AddEmployees` jako `AddEmployeesBatched` v `PostRandomEmployees` metodě volá `Employee` metodu zaúčtovat více objektů; však `AddEmployeesBatched` odešle tyto <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objekty do objektu.</span><span class="sxs-lookup"><span data-stu-id="7cb25-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="7cb25-151">Metoda `AddEmployeesBatched` také čeká na dokončení všech operací vložení.</span><span class="sxs-lookup"><span data-stu-id="7cb25-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="7cb25-152">Použití spojení ve vyrovnávací paměti ke čtení dat zaměstnanců z databáze</span><span class="sxs-lookup"><span data-stu-id="7cb25-152">Using Buffered Join to Read Employee Data from the Database</span></span>

<span data-ttu-id="7cb25-153">Přidejte `Program` do `GetRandomEmployees` třídy metodu.</span><span class="sxs-lookup"><span data-stu-id="7cb25-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

<span data-ttu-id="7cb25-154">Tato metoda vytiskne informace o náhodných zaměstnanců do konzoly.</span><span class="sxs-lookup"><span data-stu-id="7cb25-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="7cb25-155">Vytvoří několik `Employee` náhodných objektů `GetEmployeeID` a zavolá metodu k načtení jedinečného identifikátoru pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="7cb25-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="7cb25-156">Vzhledem `GetEmployeeID` k tomu, že metoda vyvolá výjimku, pokud neexistuje `GetRandomEmployees` žádný odpovídající <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> zaměstnanec `Employee` s daným `GetEmployeeID` křestním jménem a příjmení, metoda používá třídu k ukládání objektů pro úspěšná volání a <xref:System.Exception?displayProperty=nameWithType> objekty pro volání, které se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7cb25-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="7cb25-157">Objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> v tomto příkladu <xref:System.Tuple%602> působí na objekt, který obsahuje seznam `Employee` objektů a seznam <xref:System.Exception> objektů.</span><span class="sxs-lookup"><span data-stu-id="7cb25-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="7cb25-158">Objekt <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> rozšíří tato data, když se součet přijatých `Employee` a <xref:System.Exception> objektů počítá velikost dávky.</span><span class="sxs-lookup"><span data-stu-id="7cb25-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>

<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="7cb25-159">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="7cb25-159">The Complete Example</span></span>

<span data-ttu-id="7cb25-160">Následující příklad ukazuje úplný kód.</span><span class="sxs-lookup"><span data-stu-id="7cb25-160">The following example shows the complete code.</span></span> <span data-ttu-id="7cb25-161">Metoda `Main` porovnává čas, který je nutný k provedení dávkových vložení databáze oproti době provádění nedávkových vložení databáze.</span><span class="sxs-lookup"><span data-stu-id="7cb25-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="7cb25-162">Také ukazuje použití spojení ve vyrovnávací paměti ke čtení dat zaměstnanců z databáze a také sestavy chyb.</span><span class="sxs-lookup"><span data-stu-id="7cb25-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a><span data-ttu-id="7cb25-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cb25-163">See also</span></span>

- [<span data-ttu-id="7cb25-164">Tok dat</span><span class="sxs-lookup"><span data-stu-id="7cb25-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
