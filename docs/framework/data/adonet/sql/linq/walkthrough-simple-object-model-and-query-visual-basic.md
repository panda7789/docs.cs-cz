---
title: 'Návod: Jednoduchý objektový model a dotaz (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: 9bf97263bf8ae0ac3ece187e81a51edfaef48a54
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742576"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="d8c73-102">Návod: Jednoduchý objektový model a dotaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8c73-102">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>
<span data-ttu-id="d8c73-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář s minimálními složitosti.</span><span class="sxs-lookup"><span data-stu-id="d8c73-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="d8c73-104">Vytvořte třídu entity, která modeluje tabulku Customers v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="d8c73-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="d8c73-105">Pak vytvoříte jednoduchý dotaz do seznamu zákazníků, kteří jsou umístěny v Londýně.</span><span class="sxs-lookup"><span data-stu-id="d8c73-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="d8c73-106">Tento názorný postup je kód objektově orientovaný záměrné pomohou zobrazit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] koncepty.</span><span class="sxs-lookup"><span data-stu-id="d8c73-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="d8c73-107">Zpravidla, použijete Návrhář relací objektů k vytvoření objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="d8c73-107">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="d8c73-108">Tento návod byl napsán s použitím vývojového nastavení jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d8c73-108">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d8c73-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8c73-109">Prerequisites</span></span>  
  
- <span data-ttu-id="d8c73-110">Tento návod používá vyhrazené složky ("c:\linqtest") pro uložení souborů.</span><span class="sxs-lookup"><span data-stu-id="d8c73-110">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="d8c73-111">Vytvoření této složky, před zahájením návodu.</span><span class="sxs-lookup"><span data-stu-id="d8c73-111">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="d8c73-112">Tento návod vyžaduje ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="d8c73-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="d8c73-113">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="d8c73-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="d8c73-114">Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d8c73-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="d8c73-115">Po stažení databáze, zkopírujte soubor do složky c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="d8c73-115">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d8c73-116">Přehled</span><span class="sxs-lookup"><span data-stu-id="d8c73-116">Overview</span></span>  
 <span data-ttu-id="d8c73-117">Tento názorný postup se skládá z šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="d8c73-117">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="d8c73-118">Vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8c73-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="d8c73-119">Mapování třídy do databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="d8c73-119">Mapping a class to a database table.</span></span>  
  
- <span data-ttu-id="d8c73-120">Určení vlastnosti na třídu, představují sloupce databáze.</span><span class="sxs-lookup"><span data-stu-id="d8c73-120">Designating properties on the class to represent database columns.</span></span>  
  
- <span data-ttu-id="d8c73-121">Zadání připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="d8c73-121">Specifying the connection to the Northwind database.</span></span>  
  
- <span data-ttu-id="d8c73-122">Vytvoření jednoduchého dotazu ke spuštění na databázi.</span><span class="sxs-lookup"><span data-stu-id="d8c73-122">Creating a simple query to run against the database.</span></span>  
  
- <span data-ttu-id="d8c73-123">Provádění dotazu a sledování výsledky.</span><span class="sxs-lookup"><span data-stu-id="d8c73-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="d8c73-124">Vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="d8c73-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="d8c73-125">V této první úloze vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="d8c73-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="d8c73-126">K vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="d8c73-126">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="d8c73-127">Na **souboru** nabídky, klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="d8c73-127">On the **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="d8c73-128">V **typy projektů** podokně **nový projekt** dialogové okno, klikněte na tlačítko **jazyka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="d8c73-128">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="d8c73-129">V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="d8c73-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="d8c73-130">V **název** zadejte **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="d8c73-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5. <span data-ttu-id="d8c73-131">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="d8c73-131">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="d8c73-132">Přidání odkazů LINQ a direktivy</span><span class="sxs-lookup"><span data-stu-id="d8c73-132">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="d8c73-133">Tento návod používá sestavení, která nemusí být nainstalován ve výchozím nastavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="d8c73-133">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="d8c73-134">Pokud `System.Data.Linq` není uveden jako odkaz v projektu (klikněte na tlačítko **zobrazit všechny soubory** v **Průzkumníku řešení** a rozbalte **odkazy** uzlu), přidat, jak je vysvětleno v Následující kroky.</span><span class="sxs-lookup"><span data-stu-id="d8c73-134">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="d8c73-135">Chcete-li přidat System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="d8c73-135">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="d8c73-136">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="d8c73-136">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="d8c73-137">V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="d8c73-137">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d8c73-138">Sestavení se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="d8c73-138">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="d8c73-139">Také v **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, přejděte k položce a klikněte na System.Windows.Forms a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="d8c73-139">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d8c73-140">Toto sestavení, která podporuje okně se zprávou v návodu, se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="d8c73-140">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>  
  
4. <span data-ttu-id="d8c73-141">Přidejte následující direktivy výše `Module1`:</span><span class="sxs-lookup"><span data-stu-id="d8c73-141">Add the following directives above `Module1`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="d8c73-142">Mapování třídy do tabulky databáze</span><span class="sxs-lookup"><span data-stu-id="d8c73-142">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="d8c73-143">V tomto kroku vytvoříte třídu a mapovat do tabulky databáze.</span><span class="sxs-lookup"><span data-stu-id="d8c73-143">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="d8c73-144">Tato třída se nazývá *třída entity*.</span><span class="sxs-lookup"><span data-stu-id="d8c73-144">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="d8c73-145">Všimněte si, že mapování lze provést pouze přidáním <xref:System.Data.Linq.Mapping.TableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="d8c73-145">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="d8c73-146"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost určuje název tabulky v databázi.</span><span class="sxs-lookup"><span data-stu-id="d8c73-146">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="d8c73-147">Chcete-li vytvořit třídu entity a jejich mapování na tabulku databáze</span><span class="sxs-lookup"><span data-stu-id="d8c73-147">To create an entity class and map it to a database table</span></span>  
  
- <span data-ttu-id="d8c73-148">Zadejte nebo vložte následující kód do Module1.vb okamžitě výše `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="d8c73-148">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="d8c73-149">Určení vlastnosti na třídu, představují sloupce databáze</span><span class="sxs-lookup"><span data-stu-id="d8c73-149">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="d8c73-150">V tomto kroku můžete provést několik úloh.</span><span class="sxs-lookup"><span data-stu-id="d8c73-150">In this step, you accomplish several tasks.</span></span>  
  
- <span data-ttu-id="d8c73-151">Můžete použít <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení `CustomerID` a `City` vlastnosti v entitě tříd jako sloupce v tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="d8c73-151">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
- <span data-ttu-id="d8c73-152">Můžete určit `CustomerID` vlastnost jako sloupec primárního klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="d8c73-152">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
- <span data-ttu-id="d8c73-153">Určíte `_CustomerID` a `_City` polí privátního úložiště.</span><span class="sxs-lookup"><span data-stu-id="d8c73-153">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="d8c73-154">Můžete pak ukládat a načítat hodnoty přímo, namísto použití veřejnou přistupující objekty, které mohou obsahovat obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="d8c73-154">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="d8c73-155">K reprezentaci charakteristiky dva sloupce databáze</span><span class="sxs-lookup"><span data-stu-id="d8c73-155">To represent characteristics of two database columns</span></span>  
  
- <span data-ttu-id="d8c73-156">Zadejte nebo vložte následující kód do Module1.vb těsně před `End Class`:</span><span class="sxs-lookup"><span data-stu-id="d8c73-156">Type or paste the following code into Module1.vb just before `End Class`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="d8c73-157">Zadání připojení k databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="d8c73-157">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="d8c73-158">V tomto kroku použijete <xref:System.Data.Linq.DataContext> objektu k navázání připojení mezi založený na kódu datových struktur a samotná databáze.</span><span class="sxs-lookup"><span data-stu-id="d8c73-158">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="d8c73-159"><xref:System.Data.Linq.DataContext> Je hlavní kanál, přes který načtení objektů z databáze a odeslat změny.</span><span class="sxs-lookup"><span data-stu-id="d8c73-159">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="d8c73-160">Můžete také deklarovat `Table(Of Customer)` tak, aby fungoval jako tabulku logické, zadaný pro vaše dotazy na tabulku Customers v databázi.</span><span class="sxs-lookup"><span data-stu-id="d8c73-160">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="d8c73-161">Vytvoříte a spusťte tyto dotazy v dalších krocích.</span><span class="sxs-lookup"><span data-stu-id="d8c73-161">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="d8c73-162">K určení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="d8c73-162">To specify the database connection</span></span>  
  
- <span data-ttu-id="d8c73-163">Zadejte nebo vložte následující kód do `Sub Main` metody.</span><span class="sxs-lookup"><span data-stu-id="d8c73-163">Type or paste the following code into the `Sub Main` method.</span></span>  
  
     <span data-ttu-id="d8c73-164">Všimněte si, že `northwnd.mdf` soubor je považován za ve složce linqtest.</span><span class="sxs-lookup"><span data-stu-id="d8c73-164">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="d8c73-165">Další informace najdete v oddílu požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="d8c73-165">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="d8c73-166">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="d8c73-166">Creating a Simple Query</span></span>  
 <span data-ttu-id="d8c73-167">V tomto kroku vytvoříte dotaz, který najde, které zákazníkům v tabulce Zákazníci databáze jsou umístěny v Londýně.</span><span class="sxs-lookup"><span data-stu-id="d8c73-167">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="d8c73-168">Dotaz kód v tomto kroku právě popisuje dotazu.</span><span class="sxs-lookup"><span data-stu-id="d8c73-168">The query code in this step just describes the query.</span></span> <span data-ttu-id="d8c73-169">Nespustí se.</span><span class="sxs-lookup"><span data-stu-id="d8c73-169">It does not execute it.</span></span> <span data-ttu-id="d8c73-170">Tento postup se označuje jako *odložené provedení*.</span><span class="sxs-lookup"><span data-stu-id="d8c73-170">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="d8c73-171">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="d8c73-171">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="d8c73-172">Bude také vytvoří protokol výstup na zobrazení SQL příkazy, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje.</span><span class="sxs-lookup"><span data-stu-id="d8c73-172">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="d8c73-173">Tato funkce protokolování (který používá <xref:System.Data.Linq.DataContext.Log%2A>) je užitečné při ladění a určit, že příkazy odesílané do databáze přesně představovat svůj dotaz.</span><span class="sxs-lookup"><span data-stu-id="d8c73-173">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="d8c73-174">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="d8c73-174">To create a simple query</span></span>  
  
- <span data-ttu-id="d8c73-175">Zadejte nebo vložte následující kód do `Sub Main` za `Table(Of Customer)` deklarace:</span><span class="sxs-lookup"><span data-stu-id="d8c73-175">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="d8c73-176">Provádění dotazu</span><span class="sxs-lookup"><span data-stu-id="d8c73-176">Executing the Query</span></span>  
 <span data-ttu-id="d8c73-177">V tomto kroku skutečně spusťte dotaz.</span><span class="sxs-lookup"><span data-stu-id="d8c73-177">In this step, you actually execute the query.</span></span> <span data-ttu-id="d8c73-178">Výrazy dotazu, který jste vytvořili v předchozích krocích není vyhodnocen, dokud jsou potřebné výsledky.</span><span class="sxs-lookup"><span data-stu-id="d8c73-178">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="d8c73-179">Když začnete `For Each` iterace, spuštění příkazu SQL na databázi a objekty jsou vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="d8c73-179">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="d8c73-180">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="d8c73-180">To execute the query</span></span>  
  
1. <span data-ttu-id="d8c73-181">Zadejte nebo vložte následující kód na konci `Sub Main` – metoda (po description dotazu):</span><span class="sxs-lookup"><span data-stu-id="d8c73-181">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="d8c73-182">Stisknutím klávesy F5 pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d8c73-182">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d8c73-183">Pokud vaše aplikace generuje chyba za běhu, najdete v části řešení potíží [učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="d8c73-183">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="d8c73-184">Okno se zprávou zobrazí seznam šest zákazníků.</span><span class="sxs-lookup"><span data-stu-id="d8c73-184">The message box displays a list of six customers.</span></span> <span data-ttu-id="d8c73-185">V okně konzoly se zobrazí vygenerovaný kód SQL.</span><span class="sxs-lookup"><span data-stu-id="d8c73-185">The Console window displays the generated SQL code.</span></span>  
  
3. <span data-ttu-id="d8c73-186">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="d8c73-186">Click **OK** to dismiss the message box.</span></span>  
  
     <span data-ttu-id="d8c73-187">Aplikace se zavře.</span><span class="sxs-lookup"><span data-stu-id="d8c73-187">The application closes.</span></span>  
  
4. <span data-ttu-id="d8c73-188">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="d8c73-188">On the **File** menu, click **Save All**.</span></span>  
  
     <span data-ttu-id="d8c73-189">Pokud budete pokračovat s dalšího názorného postupu musíte tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d8c73-189">You will need this application if you continue with the next walkthrough.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d8c73-190">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d8c73-190">Next Steps</span></span>  
 <span data-ttu-id="d8c73-191">[Názorný postup: Dotazování napříč relacemi (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) tématu pokračuje, kde končí tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="d8c73-191">The [Walkthrough: Querying Across Relationships (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="d8c73-192">Dotazování napříč vztahy názorný postup ukazuje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete dotazování přes tabulky, podobně jako *spojení* v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="d8c73-192">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="d8c73-193">Pokud chcete provést dotazování napříč vztahy návodu, ujistěte se, že se uložit řešení pro návod, který právě jste dokončili, což je předpoklad.</span><span class="sxs-lookup"><span data-stu-id="d8c73-193">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c73-194">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8c73-194">See also</span></span>

- [<span data-ttu-id="d8c73-195">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="d8c73-195">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
