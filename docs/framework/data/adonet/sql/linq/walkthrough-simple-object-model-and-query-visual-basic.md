---
title: 'Návod: Jednoduchý objektový model a dotaz (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: a7d278dd424fbb3167a30d627379f78d0c65476f
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971789"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="f209c-102">Návod: Jednoduchý objektový model a dotaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f209c-102">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>

<span data-ttu-id="f209c-103">Tento návod poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář s minimálními složitými složitostmi.</span><span class="sxs-lookup"><span data-stu-id="f209c-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="f209c-104">Vytvoříte třídu entity, která bude modelem tabulky Customers v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f209c-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="f209c-105">Pak vytvoříte jednoduchý dotaz, který vypíše zákazníky nacházející se v Londýně.</span><span class="sxs-lookup"><span data-stu-id="f209c-105">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="f209c-106">Tento názorný postup je orientovaný na kód, který usnadňuje zobrazení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] konceptů.</span><span class="sxs-lookup"><span data-stu-id="f209c-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="f209c-107">Normálně řečeno, k vytvoření objektového modelu použijte Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="f209c-107">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="f209c-108">Tento návod byl napsán pomocí Visual Basic nastavení vývoje.</span><span class="sxs-lookup"><span data-stu-id="f209c-108">This walkthrough was written by using Visual Basic Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f209c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f209c-109">Prerequisites</span></span>

- <span data-ttu-id="f209c-110">Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest).</span><span class="sxs-lookup"><span data-stu-id="f209c-110">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="f209c-111">Před zahájením tohoto návodu vytvořte tuto složku.</span><span class="sxs-lookup"><span data-stu-id="f209c-111">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="f209c-112">Tento návod vyžaduje ukázkovou databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f209c-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="f209c-113">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f209c-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="f209c-114">Pokyny najdete v tématu [stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="f209c-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="f209c-115">Po stažení databáze zkopírujte soubor do složky c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="f209c-115">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>

## <a name="overview"></a><span data-ttu-id="f209c-116">Přehled</span><span class="sxs-lookup"><span data-stu-id="f209c-116">Overview</span></span>

<span data-ttu-id="f209c-117">Tento názorný postup se skládá ze šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="f209c-117">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="f209c-118">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Vytvoření řešení v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f209c-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="f209c-119">Mapování třídy na databázovou tabulku.</span><span class="sxs-lookup"><span data-stu-id="f209c-119">Mapping a class to a database table.</span></span>

- <span data-ttu-id="f209c-120">Určení vlastností třídy, které reprezentují sloupce databáze.</span><span class="sxs-lookup"><span data-stu-id="f209c-120">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="f209c-121">Určuje připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f209c-121">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="f209c-122">Vytvoření jednoduchého dotazu pro spuštění v databázi.</span><span class="sxs-lookup"><span data-stu-id="f209c-122">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="f209c-123">Provádění dotazu a sledování výsledků.</span><span class="sxs-lookup"><span data-stu-id="f209c-123">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="f209c-124">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f209c-124">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="f209c-125">V tomto prvním úkolu vytvoříte řešení sady Visual Studio, které obsahuje nezbytné odkazy pro sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="f209c-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="f209c-126">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f209c-126">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="f209c-127">V nabídce **soubor** klikněte na příkaz **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="f209c-127">On the **File** menu, click **New Project**.</span></span>

2. <span data-ttu-id="f209c-128">V podokně **typy projektů** v dialogovém okně **Nový projekt** klikněte na položku **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="f209c-128">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>

3. <span data-ttu-id="f209c-129">V podokně **šablony** klikněte na **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f209c-129">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="f209c-130">Do pole **název** zadejte **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="f209c-130">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="f209c-131">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="f209c-131">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="f209c-132">Přidání odkazů a direktiv LINQ</span><span class="sxs-lookup"><span data-stu-id="f209c-132">Adding LINQ References and Directives</span></span>

<span data-ttu-id="f209c-133">Tento návod používá sestavení, která nemusí být nainstalována ve výchozím nastavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="f209c-133">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="f209c-134">Pokud `System.Data.Linq` není v projektu uvedena jako odkaz (klikněte na tlačítko **Zobrazit všechny soubory** v **Průzkumník řešení** a rozbalte uzel **odkazy** ), přidejte jej, jak je vysvětleno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="f209c-134">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="f209c-135">Přidání System. data. Linq</span><span class="sxs-lookup"><span data-stu-id="f209c-135">To add System.Data.Linq</span></span>

1. <span data-ttu-id="f209c-136">V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="f209c-136">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="f209c-137">V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="f209c-137">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="f209c-138">Sestavení je přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="f209c-138">The assembly is added to the project.</span></span>

3. <span data-ttu-id="f209c-139">V dialogovém okně **Přidat odkaz** klikněte na **.NET**, přejděte na System. Windows. Forms a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="f209c-139">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>

     <span data-ttu-id="f209c-140">Toto sestavení, které podporuje okno se zprávou v návodu, je přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="f209c-140">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>

4. <span data-ttu-id="f209c-141">Níže přidejte následující direktivy `Module1`:</span><span class="sxs-lookup"><span data-stu-id="f209c-141">Add the following directives above `Module1`:</span></span>

     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="f209c-142">Mapování třídy na databázovou tabulku</span><span class="sxs-lookup"><span data-stu-id="f209c-142">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="f209c-143">V tomto kroku vytvoříte třídu a namapujete ji na databázovou tabulku.</span><span class="sxs-lookup"><span data-stu-id="f209c-143">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="f209c-144">Taková třída je označována jako *Třída entity*.</span><span class="sxs-lookup"><span data-stu-id="f209c-144">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="f209c-145">Všimněte si, že mapování je provedeno pouhým přidáním <xref:System.Data.Linq.Mapping.TableAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="f209c-145">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="f209c-146"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost určuje název tabulky v databázi.</span><span class="sxs-lookup"><span data-stu-id="f209c-146">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="f209c-147">Vytvoření třídy entity a její mapování na databázovou tabulku</span><span class="sxs-lookup"><span data-stu-id="f209c-147">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="f209c-148">Zadejte nebo vložte následující kód do Module1. vb hned výše `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="f209c-148">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>

     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="f209c-149">Určení vlastností třídy, které reprezentují sloupce databáze</span><span class="sxs-lookup"><span data-stu-id="f209c-149">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="f209c-150">V tomto kroku budete provádět několik úloh.</span><span class="sxs-lookup"><span data-stu-id="f209c-150">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="f209c-151">Použijte <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k označení `CustomerID` a `City` vlastností třídy entity jako reprezentace sloupců v databázové tabulce.</span><span class="sxs-lookup"><span data-stu-id="f209c-151">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="f209c-152">Určíte `CustomerID` vlastnost, která představuje sloupec primárního klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="f209c-152">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="f209c-153">`_CustomerID` Určíte`_City` pole pro soukromé úložiště.</span><span class="sxs-lookup"><span data-stu-id="f209c-153">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f209c-154">pak může ukládat a načítat hodnoty přímo místo použití veřejných přístupových objektů, které by mohly zahrnovat obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="f209c-154">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="f209c-155">Reprezentace vlastností dvou databázových sloupců</span><span class="sxs-lookup"><span data-stu-id="f209c-155">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="f209c-156">Zadejte nebo vložte následující kód do Module1. vb těsně před `End Class`:</span><span class="sxs-lookup"><span data-stu-id="f209c-156">Type or paste the following code into Module1.vb just before `End Class`:</span></span>

     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="f209c-157">Určení připojení k databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="f209c-157">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="f209c-158">V tomto kroku použijete <xref:System.Data.Linq.DataContext> objekt k navázání spojení mezi datovými strukturami založenými na kódu a databází samotné.</span><span class="sxs-lookup"><span data-stu-id="f209c-158">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="f209c-159"><xref:System.Data.Linq.DataContext> Je hlavním kanálem, přes který načtete objekty z databáze a odešlete změny.</span><span class="sxs-lookup"><span data-stu-id="f209c-159">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="f209c-160">Deklarujete také, `Table(Of Customer)` aby sloužil jako logická, typová tabulka pro dotazy na tabulce Customers v databázi.</span><span class="sxs-lookup"><span data-stu-id="f209c-160">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="f209c-161">Tyto dotazy budete vytvářet a spouštět v pozdějších krocích.</span><span class="sxs-lookup"><span data-stu-id="f209c-161">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="f209c-162">Určení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="f209c-162">To specify the database connection</span></span>

- <span data-ttu-id="f209c-163">Do `Sub Main` metody zadejte nebo vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="f209c-163">Type or paste the following code into the `Sub Main` method.</span></span>

     <span data-ttu-id="f209c-164">Všimněte si, `northwnd.mdf` že se předpokládá, že se soubor nachází ve složce linqtest.</span><span class="sxs-lookup"><span data-stu-id="f209c-164">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="f209c-165">Další informace najdete v části požadavky výše v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="f209c-165">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="f209c-166">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="f209c-166">Creating a Simple Query</span></span>

<span data-ttu-id="f209c-167">V tomto kroku vytvoříte dotaz pro vyhledání zákazníků v tabulce Database Customers (zákazníci), kteří se nacházejí v Londýně.</span><span class="sxs-lookup"><span data-stu-id="f209c-167">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="f209c-168">Dotazový kód v tomto kroku pouze popisuje dotaz.</span><span class="sxs-lookup"><span data-stu-id="f209c-168">The query code in this step just describes the query.</span></span> <span data-ttu-id="f209c-169">Nespustí ho.</span><span class="sxs-lookup"><span data-stu-id="f209c-169">It does not execute it.</span></span> <span data-ttu-id="f209c-170">Tento přístup se označuje jako *odložené provádění*.</span><span class="sxs-lookup"><span data-stu-id="f209c-170">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="f209c-171">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="f209c-171">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="f209c-172">Vytvoří se také výstup protokolu pro zobrazení příkazů SQL, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generují.</span><span class="sxs-lookup"><span data-stu-id="f209c-172">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="f209c-173">Tato funkce protokolování (která používá <xref:System.Data.Linq.DataContext.Log%2A>) je užitečná při ladění a při určování, zda jsou příkazy, které jsou odesílány do databáze, přesně reprezentovány vaším dotazem.</span><span class="sxs-lookup"><span data-stu-id="f209c-173">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="f209c-174">Vytvoření jednoduchého dotazu</span><span class="sxs-lookup"><span data-stu-id="f209c-174">To create a simple query</span></span>

- <span data-ttu-id="f209c-175">Zadejte nebo vložte následující kód do `Sub Main` metody `Table(Of Customer)` po deklaraci:</span><span class="sxs-lookup"><span data-stu-id="f209c-175">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>

     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]

## <a name="executing-the-query"></a><span data-ttu-id="f209c-176">Provádění dotazu</span><span class="sxs-lookup"><span data-stu-id="f209c-176">Executing the Query</span></span>

<span data-ttu-id="f209c-177">V tomto kroku ve skutečnosti spustíte dotaz.</span><span class="sxs-lookup"><span data-stu-id="f209c-177">In this step, you actually execute the query.</span></span> <span data-ttu-id="f209c-178">Výrazy dotazu, které jste vytvořili v předchozích krocích, se nevyhodnotí, dokud nebudou nutné výsledky.</span><span class="sxs-lookup"><span data-stu-id="f209c-178">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="f209c-179">Po zahájení `For Each` iterace se provede příkaz SQL pro databázi a objekty, které jsou materializované.</span><span class="sxs-lookup"><span data-stu-id="f209c-179">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="f209c-180">Provedení dotazu</span><span class="sxs-lookup"><span data-stu-id="f209c-180">To execute the query</span></span>

1. <span data-ttu-id="f209c-181">Zadejte nebo vložte následující kód na konec `Sub Main` metody (po popisu dotazu):</span><span class="sxs-lookup"><span data-stu-id="f209c-181">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>

     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]

2. <span data-ttu-id="f209c-182">Pro ladění aplikace stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="f209c-182">Press F5 to debug the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f209c-183">Pokud vaše aplikace vygeneruje chybu za běhu, přečtěte si pokyny v části věnované řešení potíží v tématu [učení](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="f209c-183">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="f209c-184">V okně se zprávou se zobrazí seznam šesti zákazníků.</span><span class="sxs-lookup"><span data-stu-id="f209c-184">The message box displays a list of six customers.</span></span> <span data-ttu-id="f209c-185">V okně konzoly se zobrazí vygenerovaný kód SQL.</span><span class="sxs-lookup"><span data-stu-id="f209c-185">The Console window displays the generated SQL code.</span></span>

3. <span data-ttu-id="f209c-186">Kliknutím na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="f209c-186">Click **OK** to dismiss the message box.</span></span>

     <span data-ttu-id="f209c-187">Aplikace se zavře.</span><span class="sxs-lookup"><span data-stu-id="f209c-187">The application closes.</span></span>

4. <span data-ttu-id="f209c-188">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="f209c-188">On the **File** menu, click **Save All**.</span></span>

     <span data-ttu-id="f209c-189">Pokud budete pokračovat v dalším návodu, budete tuto aplikaci potřebovat.</span><span class="sxs-lookup"><span data-stu-id="f209c-189">You will need this application if you continue with the next walkthrough.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f209c-190">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f209c-190">Next Steps</span></span>

<span data-ttu-id="f209c-191">[Návod: Dotazování napříč relacemi (Visual Basic](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) ) pokračuje v tom, kde tento návod skončí.</span><span class="sxs-lookup"><span data-stu-id="f209c-191">The [Walkthrough: Querying Across Relationships (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="f209c-192">Návod pro dotazování napříč relacemi ukazuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , jak se může dotazovat napříč tabulkami, podobně jako *spojení* v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="f209c-192">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="f209c-193">Pokud chcete provést dotazování napříč relacemi, nezapomeňte uložit řešení pro návod, který jste právě dokončili, což je předpoklad.</span><span class="sxs-lookup"><span data-stu-id="f209c-193">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="f209c-194">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f209c-194">See also</span></span>

- [<span data-ttu-id="f209c-195">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="f209c-195">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
