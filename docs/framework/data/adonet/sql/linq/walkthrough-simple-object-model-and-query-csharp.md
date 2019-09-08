---
title: 'Návod: Jednoduchý objektový model a dotaz (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: a9b3b57e37331cd13f2cd30b8a7663f2fb39d8c1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792127"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="15905-102">Návod: Jednoduchý objektový model a dotaz (C#)</span><span class="sxs-lookup"><span data-stu-id="15905-102">Walkthrough: Simple Object Model and Query (C#)</span></span>

<span data-ttu-id="15905-103">Tento návod poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář s minimálními složitými složitostmi.</span><span class="sxs-lookup"><span data-stu-id="15905-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="15905-104">Vytvoříte třídu entity, která bude modelem tabulky Customers v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="15905-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="15905-105">Pak vytvoříte jednoduchý dotaz, který vypíše zákazníky nacházející se v Londýně.</span><span class="sxs-lookup"><span data-stu-id="15905-105">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="15905-106">Tento názorný postup je orientovaný na kód, který usnadňuje zobrazení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] konceptů.</span><span class="sxs-lookup"><span data-stu-id="15905-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="15905-107">Normálně řečeno, k vytvoření objektového modelu použijte Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="15905-107">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="15905-108">Tento návod byl napsán s použitím nastavení C# vizuálního vývoje.</span><span class="sxs-lookup"><span data-stu-id="15905-108">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="15905-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15905-109">Prerequisites</span></span>

- <span data-ttu-id="15905-110">Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest5).</span><span class="sxs-lookup"><span data-stu-id="15905-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="15905-111">Před zahájením tohoto návodu vytvořte tuto složku.</span><span class="sxs-lookup"><span data-stu-id="15905-111">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="15905-112">Tento návod vyžaduje ukázkovou databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="15905-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="15905-113">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="15905-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="15905-114">Pokyny najdete v tématu [stažení ukázkových databází](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="15905-114">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="15905-115">Po stažení databáze zkopírujte soubor do složky c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="15905-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>

## <a name="overview"></a><span data-ttu-id="15905-116">Přehled</span><span class="sxs-lookup"><span data-stu-id="15905-116">Overview</span></span>

<span data-ttu-id="15905-117">Tento názorný postup se skládá ze šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="15905-117">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="15905-118">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Vytvoření řešení v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="15905-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="15905-119">Mapování třídy na databázovou tabulku.</span><span class="sxs-lookup"><span data-stu-id="15905-119">Mapping a class to a database table.</span></span>

- <span data-ttu-id="15905-120">Určení vlastností třídy, které reprezentují sloupce databáze.</span><span class="sxs-lookup"><span data-stu-id="15905-120">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="15905-121">Určuje připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="15905-121">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="15905-122">Vytvoření jednoduchého dotazu pro spuštění v databázi.</span><span class="sxs-lookup"><span data-stu-id="15905-122">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="15905-123">Provádění dotazu a sledování výsledků.</span><span class="sxs-lookup"><span data-stu-id="15905-123">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="15905-124">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="15905-124">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="15905-125">V tomto prvním úkolu vytvoříte řešení sady Visual Studio, které obsahuje nezbytné odkazy pro sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="15905-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="15905-126">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="15905-126">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="15905-127">V nabídce **soubor** v aplikaci Visual Studio přejděte na **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="15905-127">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="15905-128">V podokně **typy projektů** v dialogovém okně **Nový projekt** klikněte na položku **vizuál C#** .</span><span class="sxs-lookup"><span data-stu-id="15905-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="15905-129">V podokně **šablony** klikněte na **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="15905-129">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="15905-130">Do pole **název** zadejte **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="15905-130">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="15905-131">V poli **umístění** ověřte, kam chcete uložit soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="15905-131">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="15905-132">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="15905-132">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="15905-133">Přidání odkazů a direktiv LINQ</span><span class="sxs-lookup"><span data-stu-id="15905-133">Adding LINQ References and Directives</span></span>

<span data-ttu-id="15905-134">Tento návod používá sestavení, která nemusí být nainstalována ve výchozím nastavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="15905-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="15905-135">Pokud System. data. Linq není v projektu uveden jako odkaz (rozbalte uzel **odkazy** v **Průzkumník řešení**), přidejte jej, jak je vysvětleno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="15905-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="15905-136">Přidání System. data. Linq</span><span class="sxs-lookup"><span data-stu-id="15905-136">To add System.Data.Linq</span></span>

1. <span data-ttu-id="15905-137">V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="15905-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="15905-138">V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="15905-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="15905-139">Sestavení je přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="15905-139">The assembly is added to the project.</span></span>

3. <span data-ttu-id="15905-140">Do horní části **program.cs**přidejte následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="15905-140">Add the following directives at the top of **Program.cs**:</span></span>

     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="15905-141">Mapování třídy na databázovou tabulku</span><span class="sxs-lookup"><span data-stu-id="15905-141">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="15905-142">V tomto kroku vytvoříte třídu a namapujete ji na databázovou tabulku.</span><span class="sxs-lookup"><span data-stu-id="15905-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="15905-143">Taková třída je označována jako *Třída entity*.</span><span class="sxs-lookup"><span data-stu-id="15905-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="15905-144">Všimněte si, že mapování je provedeno pouhým přidáním <xref:System.Data.Linq.Mapping.TableAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="15905-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="15905-145"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost určuje název tabulky v databázi.</span><span class="sxs-lookup"><span data-stu-id="15905-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="15905-146">Vytvoření třídy entity a její mapování na databázovou tabulku</span><span class="sxs-lookup"><span data-stu-id="15905-146">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="15905-147">Zadejte nebo vložte následující kód do program.cs hned nad `Program` deklaraci třídy:</span><span class="sxs-lookup"><span data-stu-id="15905-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>

     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="15905-148">Určení vlastností třídy, které reprezentují sloupce databáze</span><span class="sxs-lookup"><span data-stu-id="15905-148">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="15905-149">V tomto kroku budete provádět několik úloh.</span><span class="sxs-lookup"><span data-stu-id="15905-149">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="15905-150">Použijte <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k označení `CustomerID` a `City` vlastností třídy entity jako reprezentace sloupců v databázové tabulce.</span><span class="sxs-lookup"><span data-stu-id="15905-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="15905-151">Určíte `CustomerID` vlastnost, která představuje sloupec primárního klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="15905-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="15905-152">`_CustomerID` Určíte`_City` pole pro soukromé úložiště.</span><span class="sxs-lookup"><span data-stu-id="15905-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="15905-153">pak může ukládat a načítat hodnoty přímo místo použití veřejných přístupových objektů, které by mohly zahrnovat obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="15905-153">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="15905-154">Reprezentace vlastností dvou databázových sloupců</span><span class="sxs-lookup"><span data-stu-id="15905-154">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="15905-155">Do program.cs do složených závorek `Customer` třídy zadejte nebo vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="15905-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>

     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="15905-156">Určení připojení k databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="15905-156">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="15905-157">V tomto kroku použijete <xref:System.Data.Linq.DataContext> objekt k navázání spojení mezi datovými strukturami založenými na kódu a databází samotné.</span><span class="sxs-lookup"><span data-stu-id="15905-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="15905-158"><xref:System.Data.Linq.DataContext> Je hlavním kanálem, přes který načtete objekty z databáze a odešlete změny.</span><span class="sxs-lookup"><span data-stu-id="15905-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="15905-159">Deklarujete také, `Table<Customer>` aby sloužil jako logická, typová tabulka pro dotazy na tabulce Customers v databázi.</span><span class="sxs-lookup"><span data-stu-id="15905-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="15905-160">Tyto dotazy budete vytvářet a spouštět v pozdějších krocích.</span><span class="sxs-lookup"><span data-stu-id="15905-160">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="15905-161">Určení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="15905-161">To specify the database connection</span></span>

- <span data-ttu-id="15905-162">Do `Main` metody zadejte nebo vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="15905-162">Type or paste the following code into the `Main` method.</span></span>

     <span data-ttu-id="15905-163">Všimněte si, `northwnd.mdf` že se předpokládá, že se soubor nachází ve složce linqtest5.</span><span class="sxs-lookup"><span data-stu-id="15905-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="15905-164">Další informace najdete v části požadavky výše v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="15905-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="15905-165">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="15905-165">Creating a Simple Query</span></span>

<span data-ttu-id="15905-166">V tomto kroku vytvoříte dotaz pro vyhledání zákazníků v tabulce Database Customers (zákazníci), kteří se nacházejí v Londýně.</span><span class="sxs-lookup"><span data-stu-id="15905-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="15905-167">Dotazový kód v tomto kroku pouze popisuje dotaz.</span><span class="sxs-lookup"><span data-stu-id="15905-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="15905-168">Nespustí ho.</span><span class="sxs-lookup"><span data-stu-id="15905-168">It does not execute it.</span></span> <span data-ttu-id="15905-169">Tento přístup se označuje jako *odložené provádění*.</span><span class="sxs-lookup"><span data-stu-id="15905-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="15905-170">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="15905-170">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="15905-171">Vytvoří se také výstup protokolu pro zobrazení příkazů SQL, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generují.</span><span class="sxs-lookup"><span data-stu-id="15905-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="15905-172">Tato funkce protokolování (která používá <xref:System.Data.Linq.DataContext.Log%2A>) je užitečná při ladění a při určování, zda jsou příkazy, které jsou odesílány do databáze, přesně reprezentovány vaším dotazem.</span><span class="sxs-lookup"><span data-stu-id="15905-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="15905-173">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="15905-173">To create a simple query</span></span>

- <span data-ttu-id="15905-174">Zadejte nebo vložte následující kód do `Main` metody `Table<Customer>` po deklaraci.</span><span class="sxs-lookup"><span data-stu-id="15905-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>

     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]

## <a name="executing-the-query"></a><span data-ttu-id="15905-175">Provádění dotazu</span><span class="sxs-lookup"><span data-stu-id="15905-175">Executing the Query</span></span>

<span data-ttu-id="15905-176">V tomto kroku ve skutečnosti spustíte dotaz.</span><span class="sxs-lookup"><span data-stu-id="15905-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="15905-177">Výrazy dotazu, které jste vytvořili v předchozích krocích, se nevyhodnotí, dokud nebudou nutné výsledky.</span><span class="sxs-lookup"><span data-stu-id="15905-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="15905-178">Po zahájení `foreach` iterace se provede příkaz SQL pro databázi a objekty, které jsou materializované.</span><span class="sxs-lookup"><span data-stu-id="15905-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="15905-179">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="15905-179">To execute the query</span></span>

1. <span data-ttu-id="15905-180">Zadejte nebo vložte následující kód na konec `Main` metody (po popisu dotazu).</span><span class="sxs-lookup"><span data-stu-id="15905-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>

     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]

2. <span data-ttu-id="15905-181">Pro ladění aplikace stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="15905-181">Press F5 to debug the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="15905-182">Pokud vaše aplikace vygeneruje chybu za běhu, přečtěte si pokyny v části věnované řešení potíží v tématu [učení](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="15905-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="15905-183">Výsledky dotazu v okně konzoly by měly vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="15905-183">The query results in the console window should appear as follows:</span></span>

     `ID=AROUT, City=London`

     `ID=BSBEV, City=London`

     `ID=CONSH, City=London`

     `ID=EASTC, City=London`

     `ID=NORTS, City=London`

     `ID=SEVES, City=London`

3. <span data-ttu-id="15905-184">V okně konzoly stiskněte klávesu ENTER, aby se aplikace zavřela.</span><span class="sxs-lookup"><span data-stu-id="15905-184">Press Enter in the console window to close the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="15905-185">Další kroky</span><span class="sxs-lookup"><span data-stu-id="15905-185">Next Steps</span></span>

<span data-ttu-id="15905-186">[Návod: Dotazování napříč relacemiC#(](walkthrough-querying-across-relationships-csharp.md) ) pokračuje v tom, kde tento návod skončí.</span><span class="sxs-lookup"><span data-stu-id="15905-186">The [Walkthrough: Querying Across Relationships (C#)](walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="15905-187">Návod dotaz napříč relacemi ukazuje, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jak se může dotazovat napříč tabulkami, podobně jako *spojení* v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="15905-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="15905-188">Pokud chcete dotaz provést napříč relacemi, nezapomeňte uložit řešení pro návod, který jste právě dokončili, což je předpoklad.</span><span class="sxs-lookup"><span data-stu-id="15905-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="15905-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15905-189">See also</span></span>

- [<span data-ttu-id="15905-190">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="15905-190">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
