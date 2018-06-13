---
title: 'Návod: Jednoduché objektový Model a dotazů (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: 2c2529c828c0b02ec2f53c7ea899bbe728ba88d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362361"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="d2919-102">Návod: Jednoduché objektový Model a dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="d2919-102">Walkthrough: Simple Object Model and Query (C#)</span></span>
<span data-ttu-id="d2919-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář s minimálním složité kroky.</span><span class="sxs-lookup"><span data-stu-id="d2919-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="d2919-104">Vytvoří třídu entity modelů tabulku zákazníků v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="d2919-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="d2919-105">Pak vytvoříte jednoduchý dotaz seznamu zákazníkům, kteří jsou umístěny v Londýně.</span><span class="sxs-lookup"><span data-stu-id="d2919-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="d2919-106">Tento názorný postup je kód orientované návrhu můžete zobrazit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] koncepty.</span><span class="sxs-lookup"><span data-stu-id="d2919-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="d2919-107">Obvykle platí, že byste použili [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vytvoření objektu modelu.</span><span class="sxs-lookup"><span data-stu-id="d2919-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="d2919-108">Tento názorný postup napsané pomocí Visual C# – vývojové nastavení.</span><span class="sxs-lookup"><span data-stu-id="d2919-108">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d2919-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2919-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="d2919-110">Tento návod používá k uložení souborů vyhrazené složky ("c:\linqtest5").</span><span class="sxs-lookup"><span data-stu-id="d2919-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="d2919-111">Než začnete návodu, vytvořte této složky.</span><span class="sxs-lookup"><span data-stu-id="d2919-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="d2919-112">Tento postup vyžaduje ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="d2919-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="d2919-113">Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="d2919-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="d2919-114">Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d2919-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="d2919-115">Po stažení databázi, zkopírujte soubor do složky c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="d2919-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d2919-116">Přehled</span><span class="sxs-lookup"><span data-stu-id="d2919-116">Overview</span></span>  
 <span data-ttu-id="d2919-117">Tento názorný postup se skládá z šesti hlavní úlohy:</span><span class="sxs-lookup"><span data-stu-id="d2919-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="d2919-118">Vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2919-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="d2919-119">Mapování třídu do databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="d2919-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="d2919-120">Určení vlastností na třídu, představují sloupců databáze.</span><span class="sxs-lookup"><span data-stu-id="d2919-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="d2919-121">Určení připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="d2919-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="d2919-122">Vytvoření jednoduchého dotazu ke spouštění na databázi.</span><span class="sxs-lookup"><span data-stu-id="d2919-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="d2919-123">Provádění dotazu a sledování výsledků.</span><span class="sxs-lookup"><span data-stu-id="d2919-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="d2919-124">Vytváření dotazu LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="d2919-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="d2919-125">V této úloze první vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="d2919-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="d2919-126">Chcete-li vytvořit LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="d2919-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="d2919-127">V sadě Visual Studio **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d2919-127">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="d2919-128">V **typy projektů** podokně **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="d2919-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="d2919-129">V **šablony** podokně klikněte na tlačítko **konzolové aplikace**.</span><span class="sxs-lookup"><span data-stu-id="d2919-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="d2919-130">V **název** zadejte **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="d2919-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="d2919-131">V **umístění** ověřte, kam chcete uložit soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="d2919-131">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="d2919-132">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="d2919-132">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="d2919-133">Přidání odkazů LINQ a direktivy</span><span class="sxs-lookup"><span data-stu-id="d2919-133">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="d2919-134">Tento návod používá sestavení, které nemusí být nainstalovány ve výchozím nastavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="d2919-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="d2919-135">Pokud System.Data.Linq není uvedena jako odkaz ve vašem projektu (rozbalte **odkazy** uzlu v **Průzkumníku řešení**), přidejte ho, jak je popsáno v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="d2919-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="d2919-136">Chcete-li přidat System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="d2919-136">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="d2919-137">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="d2919-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="d2919-138">V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="d2919-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d2919-139">Je sestavení přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="d2919-139">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="d2919-140">Přidejte následující direktivy v horní části **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="d2919-140">Add the following directives at the top of **Program.cs**:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="d2919-141">Mapování třídu do databázové tabulky</span><span class="sxs-lookup"><span data-stu-id="d2919-141">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="d2919-142">V tomto kroku vytvoříte třídu a mapovat do databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="d2919-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="d2919-143">Tato třída se říká *třídy entita*.</span><span class="sxs-lookup"><span data-stu-id="d2919-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="d2919-144">Všimněte si, že mapování lze provést pouze přidáním <xref:System.Data.Linq.Mapping.TableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="d2919-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="d2919-145"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost určuje název tabulky v databázi.</span><span class="sxs-lookup"><span data-stu-id="d2919-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="d2919-146">Vytvořte třídu entity a namapovat je do databázové tabulky</span><span class="sxs-lookup"><span data-stu-id="d2919-146">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="d2919-147">Zadejte nebo vložte následující kód do souboru Program.cs okamžitě výše `Program` deklarace třídy:</span><span class="sxs-lookup"><span data-stu-id="d2919-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="d2919-148">Určení vlastností na třídu, představují sloupců databáze</span><span class="sxs-lookup"><span data-stu-id="d2919-148">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="d2919-149">V tomto kroku můžete provést několik úloh.</span><span class="sxs-lookup"><span data-stu-id="d2919-149">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="d2919-150">Můžete použít <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení `CustomerID` a `City` vlastnosti u entity třídy představující sloupců v tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="d2919-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="d2919-151">Určíte `CustomerID` vlastnost jako představující sloupec primárního klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="d2919-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="d2919-152">Určíte `_CustomerID` a `_City` pole pro privátní úložiště.</span><span class="sxs-lookup"><span data-stu-id="d2919-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d2919-153"> Můžete pak ukládání a načítání hodnot přímo, namísto použití veřejného přístupových objektů, které mohou zahrnovat obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="d2919-153"> can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="d2919-154">Představují charakteristiky dvou sloupců databáze</span><span class="sxs-lookup"><span data-stu-id="d2919-154">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="d2919-155">Zadejte nebo vložte následující kód do souboru Program.cs uvnitř složených závorek pro `Customer` třídy.</span><span class="sxs-lookup"><span data-stu-id="d2919-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="d2919-156">Určení připojení k databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="d2919-156">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="d2919-157">V tomto kroku použijete <xref:System.Data.Linq.DataContext> objektu k navázání připojení mezi vaší založené na kódu datové struktury a samotná databáze.</span><span class="sxs-lookup"><span data-stu-id="d2919-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="d2919-158"><xref:System.Data.Linq.DataContext> Je hlavní kanál, pomocí kterého se načtení objektů z databáze a odeslání změn.</span><span class="sxs-lookup"><span data-stu-id="d2919-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="d2919-159">Je také deklarovat `Table<Customer>` tak, aby fungoval jako logické, typu tabulky pro vaše dotazy pro tabulku zákazníků v databázi.</span><span class="sxs-lookup"><span data-stu-id="d2919-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="d2919-160">Vytvoříte a spusťte tyto dotazy v dalších krocích.</span><span class="sxs-lookup"><span data-stu-id="d2919-160">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="d2919-161">K určení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="d2919-161">To specify the database connection</span></span>  
  
-   <span data-ttu-id="d2919-162">Zadejte nebo vložte následující kód do `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="d2919-162">Type or paste the following code into the `Main` method.</span></span>  
  
     <span data-ttu-id="d2919-163">Všimněte si, že `northwnd.mdf` souboru se předpokládá, že se ve složce linqtest5.</span><span class="sxs-lookup"><span data-stu-id="d2919-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="d2919-164">Další informace najdete v části požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="d2919-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="d2919-165">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="d2919-165">Creating a Simple Query</span></span>  
 <span data-ttu-id="d2919-166">V tomto kroku vytvoříte dotaz, který najde v tabulce databáze zákazníci uvedeni zákazníci, kteří jsou umístěny v Londýně.</span><span class="sxs-lookup"><span data-stu-id="d2919-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="d2919-167">Kód dotazu v tomto kroku právě popisuje dotaz.</span><span class="sxs-lookup"><span data-stu-id="d2919-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="d2919-168">Ho ji není provedena.</span><span class="sxs-lookup"><span data-stu-id="d2919-168">It does not execute it.</span></span> <span data-ttu-id="d2919-169">Tento postup se označuje jako *odložené spouštění*.</span><span class="sxs-lookup"><span data-stu-id="d2919-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="d2919-170">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="d2919-170">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="d2919-171">Budete také produktu protokolu výstup zobrazíte SQL příkazy, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje.</span><span class="sxs-lookup"><span data-stu-id="d2919-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="d2919-172">Tato funkce protokolování (které používá <xref:System.Data.Linq.DataContext.Log%2A>) je užitečné v ladění a určení, že příkazy odesílány do databáze přesně představují dotazu.</span><span class="sxs-lookup"><span data-stu-id="d2919-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="d2919-173">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="d2919-173">To create a simple query</span></span>  
  
-   <span data-ttu-id="d2919-174">Zadejte nebo vložte následující kód do `Main` metoda po `Table<Customer>` deklarace.</span><span class="sxs-lookup"><span data-stu-id="d2919-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="d2919-175">Provádění dotazu</span><span class="sxs-lookup"><span data-stu-id="d2919-175">Executing the Query</span></span>  
 <span data-ttu-id="d2919-176">V tomto kroku skutečně provést dotaz.</span><span class="sxs-lookup"><span data-stu-id="d2919-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="d2919-177">Výrazy dotazů, které jste vytvořili v předchozích krocích nebudou vyhodnoceny, dokud jsou potřeba výsledky.</span><span class="sxs-lookup"><span data-stu-id="d2919-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="d2919-178">Když začnete `foreach` iterace, je spustit příkaz SQL pro databázi a objekty jsou materializována.</span><span class="sxs-lookup"><span data-stu-id="d2919-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="d2919-179">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="d2919-179">To execute the query</span></span>  
  
1.  <span data-ttu-id="d2919-180">Zadejte nebo vložte následující kód na konci `Main` – metoda (po popis dotazu).</span><span class="sxs-lookup"><span data-stu-id="d2919-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="d2919-181">Stisknutím klávesy F5 ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2919-181">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2919-182">Pokud vaše aplikace generuje chyba spuštění, naleznete v části řešení potíží [učení podle návody](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="d2919-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="d2919-183">Výsledky dotazu v okně konzoly se zobrazí následující:</span><span class="sxs-lookup"><span data-stu-id="d2919-183">The query results in the console window should appear as follows:</span></span>  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  <span data-ttu-id="d2919-184">Stisknutím klávesy Enter v okně konzoly aplikace se zavře.</span><span class="sxs-lookup"><span data-stu-id="d2919-184">Press Enter in the console window to close the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d2919-185">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d2919-185">Next Steps</span></span>  
 <span data-ttu-id="d2919-186">[Návod: dotazování napříč vztahy (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) tématu pokračuje, které končí tento návod.</span><span class="sxs-lookup"><span data-stu-id="d2919-186">The [Walkthrough: Querying Across Relationships (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="d2919-187">Dotaz napříč vztahy návod ukazuje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete dotazování mezi tabulkami, podobně jako *spojení* v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="d2919-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="d2919-188">Pokud chcete do dotazu napříč vztahy návod, uložte řešení pro, který právě jste dokončili Průvodce, který je podmínkou.</span><span class="sxs-lookup"><span data-stu-id="d2919-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2919-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2919-189">See Also</span></span>  
 [<span data-ttu-id="d2919-190">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="d2919-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
