---
title: 'Návod: Jednoduchý objektový model a dotaz (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: dc56f1e7886a1a1391d94b512ba5c91ca8c9092a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59309456"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="7238a-102">Návod: Jednoduchý objektový model a dotaz (C#)</span><span class="sxs-lookup"><span data-stu-id="7238a-102">Walkthrough: Simple Object Model and Query (C#)</span></span>
<span data-ttu-id="7238a-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář s minimálními složitosti.</span><span class="sxs-lookup"><span data-stu-id="7238a-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="7238a-104">Vytvořte třídu entity, která modeluje tabulku Customers v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="7238a-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="7238a-105">Pak vytvoříte jednoduchý dotaz do seznamu zákazníků, kteří jsou umístěny v Londýně.</span><span class="sxs-lookup"><span data-stu-id="7238a-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="7238a-106">Tento názorný postup je kód objektově orientovaný záměrné pomohou zobrazit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] koncepty.</span><span class="sxs-lookup"><span data-stu-id="7238a-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="7238a-107">Obvykle vzato můžete využít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vytvoření objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="7238a-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="7238a-108">Tento návod byl napsán s použitím Visual C# vývojovým nastavením.</span><span class="sxs-lookup"><span data-stu-id="7238a-108">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7238a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7238a-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="7238a-110">Tento návod používá vyhrazené složky ("c:\linqtest5") pro uložení souborů.</span><span class="sxs-lookup"><span data-stu-id="7238a-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="7238a-111">Vytvoření této složky, před zahájením návodu.</span><span class="sxs-lookup"><span data-stu-id="7238a-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="7238a-112">Tento návod vyžaduje ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="7238a-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="7238a-113">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="7238a-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="7238a-114">Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="7238a-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="7238a-115">Po stažení databáze, zkopírujte soubor do složky c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="7238a-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="7238a-116">Přehled</span><span class="sxs-lookup"><span data-stu-id="7238a-116">Overview</span></span>  
 <span data-ttu-id="7238a-117">Tento názorný postup se skládá z šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="7238a-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="7238a-118">Vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7238a-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="7238a-119">Mapování třídy do databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="7238a-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="7238a-120">Určení vlastnosti na třídu, představují sloupce databáze.</span><span class="sxs-lookup"><span data-stu-id="7238a-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="7238a-121">Zadání připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="7238a-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="7238a-122">Vytvoření jednoduchého dotazu ke spuštění na databázi.</span><span class="sxs-lookup"><span data-stu-id="7238a-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="7238a-123">Provádění dotazu a sledování výsledky.</span><span class="sxs-lookup"><span data-stu-id="7238a-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="7238a-124">Vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="7238a-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="7238a-125">V této první úloze vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="7238a-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="7238a-126">K vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="7238a-126">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="7238a-127">V sadě Visual Studio **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="7238a-127">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="7238a-128">V **typy projektů** podokně **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#** .</span><span class="sxs-lookup"><span data-stu-id="7238a-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="7238a-129">V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="7238a-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="7238a-130">V **název** zadejte **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="7238a-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5. <span data-ttu-id="7238a-131">V **umístění** pole, ověřte, kam chcete uložit soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="7238a-131">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="7238a-132">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="7238a-132">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="7238a-133">Přidání odkazů LINQ a direktivy</span><span class="sxs-lookup"><span data-stu-id="7238a-133">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="7238a-134">Tento návod používá sestavení, která nemusí být nainstalován ve výchozím nastavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="7238a-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="7238a-135">Pokud System.Data.Linq není uveden jako odkaz v projektu (rozšířit **odkazy** uzel v **Průzkumníku řešení**), přidat, jak je popsáno v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="7238a-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="7238a-136">Chcete-li přidat System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="7238a-136">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="7238a-137">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="7238a-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="7238a-138">V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="7238a-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7238a-139">Sestavení se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="7238a-139">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="7238a-140">Přidejte následující direktivy v horní části **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="7238a-140">Add the following directives at the top of **Program.cs**:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="7238a-141">Mapování třídy do tabulky databáze</span><span class="sxs-lookup"><span data-stu-id="7238a-141">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="7238a-142">V tomto kroku vytvoříte třídu a mapovat do tabulky databáze.</span><span class="sxs-lookup"><span data-stu-id="7238a-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="7238a-143">Tato třída se nazývá *třída entity*.</span><span class="sxs-lookup"><span data-stu-id="7238a-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="7238a-144">Všimněte si, že mapování lze provést pouze přidáním <xref:System.Data.Linq.Mapping.TableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="7238a-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="7238a-145"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost určuje název tabulky v databázi.</span><span class="sxs-lookup"><span data-stu-id="7238a-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="7238a-146">Chcete-li vytvořit třídu entity a jejich mapování na tabulku databáze</span><span class="sxs-lookup"><span data-stu-id="7238a-146">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="7238a-147">Zadejte nebo vložte následující kód do souboru Program.cs okamžitě výše `Program` deklarace třídy:</span><span class="sxs-lookup"><span data-stu-id="7238a-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="7238a-148">Určení vlastnosti na třídu, představují sloupce databáze</span><span class="sxs-lookup"><span data-stu-id="7238a-148">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="7238a-149">V tomto kroku můžete provést několik úloh.</span><span class="sxs-lookup"><span data-stu-id="7238a-149">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="7238a-150">Můžete použít <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení `CustomerID` a `City` vlastnosti v entitě tříd jako sloupce v tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="7238a-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="7238a-151">Můžete určit `CustomerID` vlastnost jako sloupec primárního klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="7238a-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="7238a-152">Určíte `_CustomerID` a `_City` polí privátního úložiště.</span><span class="sxs-lookup"><span data-stu-id="7238a-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7238a-153">Můžete pak ukládat a načítat hodnoty přímo, namísto použití veřejnou přistupující objekty, které mohou obsahovat obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="7238a-153">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="7238a-154">K reprezentaci charakteristiky dva sloupce databáze</span><span class="sxs-lookup"><span data-stu-id="7238a-154">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="7238a-155">Zadejte nebo vložte následující kód do souboru Program.cs uvnitř složených závorek pro `Customer` třídy.</span><span class="sxs-lookup"><span data-stu-id="7238a-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="7238a-156">Zadání připojení k databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="7238a-156">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="7238a-157">V tomto kroku použijete <xref:System.Data.Linq.DataContext> objektu k navázání připojení mezi založený na kódu datových struktur a samotná databáze.</span><span class="sxs-lookup"><span data-stu-id="7238a-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="7238a-158"><xref:System.Data.Linq.DataContext> Je hlavní kanál, přes který načtení objektů z databáze a odeslat změny.</span><span class="sxs-lookup"><span data-stu-id="7238a-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="7238a-159">Můžete také deklarovat `Table<Customer>` tak, aby fungoval jako tabulku logické, zadaný pro vaše dotazy na tabulku Customers v databázi.</span><span class="sxs-lookup"><span data-stu-id="7238a-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="7238a-160">Vytvoříte a spusťte tyto dotazy v dalších krocích.</span><span class="sxs-lookup"><span data-stu-id="7238a-160">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="7238a-161">K určení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="7238a-161">To specify the database connection</span></span>  
  
-   <span data-ttu-id="7238a-162">Zadejte nebo vložte následující kód do `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="7238a-162">Type or paste the following code into the `Main` method.</span></span>  
  
     <span data-ttu-id="7238a-163">Všimněte si, že `northwnd.mdf` soubor je považován za ve složce linqtest5.</span><span class="sxs-lookup"><span data-stu-id="7238a-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="7238a-164">Další informace najdete v oddílu požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="7238a-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="7238a-165">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="7238a-165">Creating a Simple Query</span></span>  
 <span data-ttu-id="7238a-166">V tomto kroku vytvoříte dotaz, který najde, které zákazníkům v tabulce Zákazníci databáze jsou umístěny v Londýně.</span><span class="sxs-lookup"><span data-stu-id="7238a-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="7238a-167">Dotaz kód v tomto kroku právě popisuje dotazu.</span><span class="sxs-lookup"><span data-stu-id="7238a-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="7238a-168">Nespustí se.</span><span class="sxs-lookup"><span data-stu-id="7238a-168">It does not execute it.</span></span> <span data-ttu-id="7238a-169">Tento postup se označuje jako *odložené provedení*.</span><span class="sxs-lookup"><span data-stu-id="7238a-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="7238a-170">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="7238a-170">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="7238a-171">Bude také vytvoří protokol výstup na zobrazení SQL příkazy, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje.</span><span class="sxs-lookup"><span data-stu-id="7238a-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="7238a-172">Tato funkce protokolování (který používá <xref:System.Data.Linq.DataContext.Log%2A>) je užitečné při ladění a určit, že příkazy odesílané do databáze přesně představovat svůj dotaz.</span><span class="sxs-lookup"><span data-stu-id="7238a-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="7238a-173">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="7238a-173">To create a simple query</span></span>  
  
-   <span data-ttu-id="7238a-174">Zadejte nebo vložte následující kód do `Main` za `Table<Customer>` deklarace.</span><span class="sxs-lookup"><span data-stu-id="7238a-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="7238a-175">Provádění dotazu</span><span class="sxs-lookup"><span data-stu-id="7238a-175">Executing the Query</span></span>  
 <span data-ttu-id="7238a-176">V tomto kroku skutečně spusťte dotaz.</span><span class="sxs-lookup"><span data-stu-id="7238a-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="7238a-177">Výrazy dotazu, který jste vytvořili v předchozích krocích není vyhodnocen, dokud jsou potřebné výsledky.</span><span class="sxs-lookup"><span data-stu-id="7238a-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="7238a-178">Když začnete `foreach` iterace, spuštění příkazu SQL na databázi a objekty jsou vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="7238a-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="7238a-179">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="7238a-179">To execute the query</span></span>  
  
1. <span data-ttu-id="7238a-180">Zadejte nebo vložte následující kód na konci `Main` – metoda (po description dotazu).</span><span class="sxs-lookup"><span data-stu-id="7238a-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2. <span data-ttu-id="7238a-181">Stisknutím klávesy F5 pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="7238a-181">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7238a-182">Pokud vaše aplikace generuje chyba za běhu, najdete v části řešení potíží [učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="7238a-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="7238a-183">Výsledky dotazu v okně konzoly by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7238a-183">The query results in the console window should appear as follows:</span></span>  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3. <span data-ttu-id="7238a-184">Stisknutím klávesy Enter ukončete aplikaci v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="7238a-184">Press Enter in the console window to close the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7238a-185">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7238a-185">Next Steps</span></span>  
 <span data-ttu-id="7238a-186">[Názorný postup: Dotazování napříč vztahy (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) tématu pokračuje, kde končí tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="7238a-186">The [Walkthrough: Querying Across Relationships (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="7238a-187">Dotaz napříč vztahy názorný postup ukazuje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete dotazování přes tabulky, podobně jako *spojení* v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="7238a-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="7238a-188">Pokud chcete provést dotaz napříč vztahy návodu se ujistěte, že se uložit řešení pro návod, který právě jste dokončili, což je předpoklad.</span><span class="sxs-lookup"><span data-stu-id="7238a-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7238a-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7238a-189">See also</span></span>

- [<span data-ttu-id="7238a-190">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="7238a-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
