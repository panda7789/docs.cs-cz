---
title: 'Návod: Jednoduché objektový Model a dotazů (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: f2df0dfa039fa37fd9d9b471d28b2a03f06b3037
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365732"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="c099d-102">Návod: Jednoduché objektový Model a dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c099d-102">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>
<span data-ttu-id="c099d-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář s minimálním složité kroky.</span><span class="sxs-lookup"><span data-stu-id="c099d-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="c099d-104">Vytvoří třídu entity modelů tabulku zákazníků v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="c099d-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="c099d-105">Pak vytvoříte jednoduchý dotaz seznamu zákazníkům, kteří jsou umístěny v Londýně.</span><span class="sxs-lookup"><span data-stu-id="c099d-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="c099d-106">Tento názorný postup je kód orientované návrhu můžete zobrazit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] koncepty.</span><span class="sxs-lookup"><span data-stu-id="c099d-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="c099d-107">Obvykle platí, že byste použili [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vytvoření objektu modelu.</span><span class="sxs-lookup"><span data-stu-id="c099d-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="c099d-108">Tento názorný postup napsané pomocí jazyka Visual Basic – vývojové nastavení.</span><span class="sxs-lookup"><span data-stu-id="c099d-108">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c099d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c099d-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="c099d-110">Tento návod používá k uložení souborů vyhrazené složky ("c:\linqtest").</span><span class="sxs-lookup"><span data-stu-id="c099d-110">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="c099d-111">Než začnete návodu, vytvořte této složky.</span><span class="sxs-lookup"><span data-stu-id="c099d-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="c099d-112">Tento postup vyžaduje ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="c099d-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="c099d-113">Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="c099d-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="c099d-114">Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c099d-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="c099d-115">Po stažení databázi, zkopírujte soubor do složky c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="c099d-115">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c099d-116">Přehled</span><span class="sxs-lookup"><span data-stu-id="c099d-116">Overview</span></span>  
 <span data-ttu-id="c099d-117">Tento názorný postup se skládá z šesti hlavní úlohy:</span><span class="sxs-lookup"><span data-stu-id="c099d-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="c099d-118">Vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c099d-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="c099d-119">Mapování třídu do databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="c099d-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="c099d-120">Určení vlastností na třídu, představují sloupců databáze.</span><span class="sxs-lookup"><span data-stu-id="c099d-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="c099d-121">Určení připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="c099d-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="c099d-122">Vytvoření jednoduchého dotazu ke spouštění na databázi.</span><span class="sxs-lookup"><span data-stu-id="c099d-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="c099d-123">Provádění dotazu a sledování výsledků.</span><span class="sxs-lookup"><span data-stu-id="c099d-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="c099d-124">Vytváření dotazu LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="c099d-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="c099d-125">V této úloze první vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="c099d-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="c099d-126">Chcete-li vytvořit LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="c099d-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="c099d-127">Na **soubor** nabídky, klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="c099d-127">On the **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="c099d-128">V **typy projektů** podokně **nový projekt** dialogové okno, klikněte na tlačítko **jazyka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="c099d-128">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3.  <span data-ttu-id="c099d-129">V **šablony** podokně klikněte na tlačítko **konzolové aplikace**.</span><span class="sxs-lookup"><span data-stu-id="c099d-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="c099d-130">V **název** zadejte **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="c099d-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="c099d-131">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="c099d-131">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="c099d-132">Přidání odkazů LINQ a direktivy</span><span class="sxs-lookup"><span data-stu-id="c099d-132">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="c099d-133">Tento návod používá sestavení, které nemusí být nainstalovány ve výchozím nastavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="c099d-133">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="c099d-134">Pokud `System.Data.Linq` není uvedena jako odkaz ve vašem projektu (klikněte na tlačítko **zobrazit všechny soubory** v **Průzkumníku řešení** a rozbalte **odkazy** uzlu), přidat, jak je popsáno v Následující kroky.</span><span class="sxs-lookup"><span data-stu-id="c099d-134">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="c099d-135">Chcete-li přidat System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="c099d-135">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="c099d-136">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="c099d-136">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="c099d-137">V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c099d-137">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c099d-138">Je sestavení přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="c099d-138">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="c099d-139">Také v **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, přejděte na a klikněte na tlačítko System.Windows.Forms a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c099d-139">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c099d-140">Toto sestavení, která podporuje pole zpráv v tomto návodu, se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="c099d-140">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>  
  
4.  <span data-ttu-id="c099d-141">Přidejte následující direktivy výše `Module1`:</span><span class="sxs-lookup"><span data-stu-id="c099d-141">Add the following directives above `Module1`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="c099d-142">Mapování třídu do databázové tabulky</span><span class="sxs-lookup"><span data-stu-id="c099d-142">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="c099d-143">V tomto kroku vytvoříte třídu a mapovat do databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="c099d-143">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="c099d-144">Tato třída se říká *třídy entita*.</span><span class="sxs-lookup"><span data-stu-id="c099d-144">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="c099d-145">Všimněte si, že mapování lze provést pouze přidáním <xref:System.Data.Linq.Mapping.TableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="c099d-145">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="c099d-146"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost určuje název tabulky v databázi.</span><span class="sxs-lookup"><span data-stu-id="c099d-146">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="c099d-147">Vytvořte třídu entity a namapovat je do databázové tabulky</span><span class="sxs-lookup"><span data-stu-id="c099d-147">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="c099d-148">Zadejte nebo vložte následující kód do Module1.vb okamžitě výše `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="c099d-148">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="c099d-149">Určení vlastností na třídu, představují sloupců databáze</span><span class="sxs-lookup"><span data-stu-id="c099d-149">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="c099d-150">V tomto kroku můžete provést několik úloh.</span><span class="sxs-lookup"><span data-stu-id="c099d-150">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="c099d-151">Můžete použít <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení `CustomerID` a `City` vlastnosti u entity třídy představující sloupců v tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="c099d-151">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="c099d-152">Určíte `CustomerID` vlastnost jako představující sloupec primárního klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="c099d-152">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="c099d-153">Určíte `_CustomerID` a `_City` pole pro privátní úložiště.</span><span class="sxs-lookup"><span data-stu-id="c099d-153">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c099d-154"> Můžete pak ukládání a načítání hodnot přímo, namísto použití veřejného přístupových objektů, které mohou zahrnovat obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="c099d-154"> can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="c099d-155">Představují charakteristiky dvou sloupců databáze</span><span class="sxs-lookup"><span data-stu-id="c099d-155">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="c099d-156">Zadejte nebo vložte následující kód do Module1.vb těsně před `End Class`:</span><span class="sxs-lookup"><span data-stu-id="c099d-156">Type or paste the following code into Module1.vb just before `End Class`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="c099d-157">Určení připojení k databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="c099d-157">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="c099d-158">V tomto kroku použijete <xref:System.Data.Linq.DataContext> objektu k navázání připojení mezi vaší založené na kódu datové struktury a samotná databáze.</span><span class="sxs-lookup"><span data-stu-id="c099d-158">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="c099d-159"><xref:System.Data.Linq.DataContext> Je hlavní kanál, pomocí kterého se načtení objektů z databáze a odeslání změn.</span><span class="sxs-lookup"><span data-stu-id="c099d-159">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="c099d-160">Je také deklarovat `Table(Of Customer)` tak, aby fungoval jako logické, typu tabulky pro vaše dotazy pro tabulku zákazníků v databázi.</span><span class="sxs-lookup"><span data-stu-id="c099d-160">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="c099d-161">Vytvoříte a spusťte tyto dotazy v dalších krocích.</span><span class="sxs-lookup"><span data-stu-id="c099d-161">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="c099d-162">K určení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="c099d-162">To specify the database connection</span></span>  
  
-   <span data-ttu-id="c099d-163">Zadejte nebo vložte následující kód do `Sub Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="c099d-163">Type or paste the following code into the `Sub Main` method.</span></span>  
  
     <span data-ttu-id="c099d-164">Všimněte si, že `northwnd.mdf` souboru se předpokládá, že se ve složce linqtest.</span><span class="sxs-lookup"><span data-stu-id="c099d-164">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="c099d-165">Další informace najdete v části požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="c099d-165">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="c099d-166">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="c099d-166">Creating a Simple Query</span></span>  
 <span data-ttu-id="c099d-167">V tomto kroku vytvoříte dotaz, který najde v tabulce databáze zákazníci uvedeni zákazníci, kteří jsou umístěny v Londýně.</span><span class="sxs-lookup"><span data-stu-id="c099d-167">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="c099d-168">Kód dotazu v tomto kroku právě popisuje dotaz.</span><span class="sxs-lookup"><span data-stu-id="c099d-168">The query code in this step just describes the query.</span></span> <span data-ttu-id="c099d-169">Ho ji není provedena.</span><span class="sxs-lookup"><span data-stu-id="c099d-169">It does not execute it.</span></span> <span data-ttu-id="c099d-170">Tento postup se označuje jako *odložené spouštění*.</span><span class="sxs-lookup"><span data-stu-id="c099d-170">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="c099d-171">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="c099d-171">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="c099d-172">Budete také produktu protokolu výstup zobrazíte SQL příkazy, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje.</span><span class="sxs-lookup"><span data-stu-id="c099d-172">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="c099d-173">Tato funkce protokolování (které používá <xref:System.Data.Linq.DataContext.Log%2A>) je užitečné v ladění a určení, že příkazy odesílány do databáze přesně představují dotazu.</span><span class="sxs-lookup"><span data-stu-id="c099d-173">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="c099d-174">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="c099d-174">To create a simple query</span></span>  
  
-   <span data-ttu-id="c099d-175">Zadejte nebo vložte následující kód do `Sub Main` metoda po `Table(Of Customer)` deklarace:</span><span class="sxs-lookup"><span data-stu-id="c099d-175">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="c099d-176">Provádění dotazu</span><span class="sxs-lookup"><span data-stu-id="c099d-176">Executing the Query</span></span>  
 <span data-ttu-id="c099d-177">V tomto kroku skutečně provést dotaz.</span><span class="sxs-lookup"><span data-stu-id="c099d-177">In this step, you actually execute the query.</span></span> <span data-ttu-id="c099d-178">Výrazy dotazů, které jste vytvořili v předchozích krocích nebudou vyhodnoceny, dokud jsou potřeba výsledky.</span><span class="sxs-lookup"><span data-stu-id="c099d-178">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="c099d-179">Když začnete `For Each` iterace, je spustit příkaz SQL pro databázi a objekty jsou materializována.</span><span class="sxs-lookup"><span data-stu-id="c099d-179">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="c099d-180">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="c099d-180">To execute the query</span></span>  
  
1.  <span data-ttu-id="c099d-181">Zadejte nebo vložte následující kód na konci `Sub Main` – metoda (po popis dotazu):</span><span class="sxs-lookup"><span data-stu-id="c099d-181">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2.  <span data-ttu-id="c099d-182">Stisknutím klávesy F5 ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c099d-182">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c099d-183">Pokud vaše aplikace generuje chyba spuštění, naleznete v části řešení potíží [učení podle návody](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="c099d-183">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="c099d-184">Do pole zpráva zobrazí seznam šesti zákazníků.</span><span class="sxs-lookup"><span data-stu-id="c099d-184">The message box displays a list of six customers.</span></span> <span data-ttu-id="c099d-185">V okně konzoly zobrazí generovaného kódu SQL.</span><span class="sxs-lookup"><span data-stu-id="c099d-185">The Console window displays the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="c099d-186">Klikněte na tlačítko **OK** se zavřít okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="c099d-186">Click **OK** to dismiss the message box.</span></span>  
  
     <span data-ttu-id="c099d-187">Aplikace se ukončí.</span><span class="sxs-lookup"><span data-stu-id="c099d-187">The application closes.</span></span>  
  
4.  <span data-ttu-id="c099d-188">Na **soubor** nabídky, klikněte na tlačítko **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="c099d-188">On the **File** menu, click **Save All**.</span></span>  
  
     <span data-ttu-id="c099d-189">Je nutné tuto aplikaci, pokud budete pokračovat další návod.</span><span class="sxs-lookup"><span data-stu-id="c099d-189">You will need this application if you continue with the next walkthrough.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c099d-190">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c099d-190">Next Steps</span></span>  
 <span data-ttu-id="c099d-191">[Návod: dotazování napříč vztahy (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) tématu pokračuje, které končí tento návod.</span><span class="sxs-lookup"><span data-stu-id="c099d-191">The [Walkthrough: Querying Across Relationships (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="c099d-192">Dotazování napříč vztahy návod ukazuje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete dotazování mezi tabulkami, podobně jako *spojení* v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="c099d-192">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="c099d-193">Pokud chcete postupovat podle návodu dotazování napříč vztahy, uložte řešení pro, který právě jste dokončili Průvodce, který je podmínkou.</span><span class="sxs-lookup"><span data-stu-id="c099d-193">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c099d-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="c099d-194">See Also</span></span>  
 [<span data-ttu-id="c099d-195">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="c099d-195">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
