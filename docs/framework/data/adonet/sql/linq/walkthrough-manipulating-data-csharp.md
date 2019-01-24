---
title: 'Průvodce: Manipulace s daty (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: a4346479337820f33cc908c0fd191ee7258a3db6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637304"
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="428c0-102">Průvodce: Manipulace s daty (C#)</span><span class="sxs-lookup"><span data-stu-id="428c0-102">Walkthrough: Manipulating Data (C#)</span></span>
<span data-ttu-id="428c0-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravy a odstraňování dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="428c0-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="428c0-104">Přidejte zákazníka, změňte název zákazníka a odstranit objednávky použijete kopii ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="428c0-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="428c0-105">Tento návod byl napsán s použitím Visual C# vývojovým nastavením.</span><span class="sxs-lookup"><span data-stu-id="428c0-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="428c0-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="428c0-106">Prerequisites</span></span>  
 <span data-ttu-id="428c0-107">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="428c0-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="428c0-108">Tento návod používá vyhrazené složky ("c:\linqtest6") pro uložení souborů.</span><span class="sxs-lookup"><span data-stu-id="428c0-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="428c0-109">Vytvoření této složky, před zahájením návodu.</span><span class="sxs-lookup"><span data-stu-id="428c0-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="428c0-110">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="428c0-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="428c0-111">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="428c0-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="428c0-112">Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="428c0-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="428c0-113">Po stažení databáze, zkopírujte do složky c:\linqtest6 northwnd.mdf souboru.</span><span class="sxs-lookup"><span data-stu-id="428c0-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
-   <span data-ttu-id="428c0-114">A C# soubor kód generovaný z databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="428c0-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="428c0-115">Tento soubor můžete vygenerovat buď pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo nástroji SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="428c0-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="428c0-116">Tento návod byl napsán s použitím nástroje SQLMetal s následujícím příkazovým řádkem:</span><span class="sxs-lookup"><span data-stu-id="428c0-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="428c0-117">**SqlMetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" / pluralize**</span><span class="sxs-lookup"><span data-stu-id="428c0-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="428c0-118">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="428c0-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="428c0-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="428c0-119">Overview</span></span>  
 <span data-ttu-id="428c0-120">Tento názorný postup se skládá z šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="428c0-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="428c0-121">Vytváří [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="428c0-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="428c0-122">Přidání kódu databázový soubor do projektu.</span><span class="sxs-lookup"><span data-stu-id="428c0-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="428c0-123">Vytváří se nový objekt zákazníka.</span><span class="sxs-lookup"><span data-stu-id="428c0-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="428c0-124">Úprava kontaktní jméno zákazníka.</span><span class="sxs-lookup"><span data-stu-id="428c0-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="428c0-125">Odstraňuje se objednávky.</span><span class="sxs-lookup"><span data-stu-id="428c0-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="428c0-126">Odesílá se tyto změny k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="428c0-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="428c0-127">Vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="428c0-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="428c0-128">V této první úloze vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="428c0-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="428c0-129">K vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="428c0-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="428c0-130">V sadě Visual Studio **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="428c0-130">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="428c0-131">V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#** .</span><span class="sxs-lookup"><span data-stu-id="428c0-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="428c0-132">V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="428c0-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="428c0-133">V **název** zadejte **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="428c0-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="428c0-134">V **umístění** pole, ověřte, kam chcete uložit soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="428c0-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="428c0-135">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="428c0-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="428c0-136">Přidání odkazů LINQ a direktivy</span><span class="sxs-lookup"><span data-stu-id="428c0-136">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="428c0-137">Tento návod používá sestavení, která nemusí být nainstalován ve výchozím nastavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="428c0-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="428c0-138">Pokud System.Data.Linq není uveden jako odkaz v projektu, přidejte ji tak, jak je popsáno v následujících krocích:</span><span class="sxs-lookup"><span data-stu-id="428c0-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="428c0-139">Chcete-li přidat System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="428c0-139">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="428c0-140">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="428c0-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="428c0-141">V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="428c0-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="428c0-142">Sestavení se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="428c0-142">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="428c0-143">V horní části souboru program.cs přidejte následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="428c0-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="428c0-144">Přidání souboru Northwind kódu do projektu</span><span class="sxs-lookup"><span data-stu-id="428c0-144">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="428c0-145">Tento postup předpokládá, že jste použili nástroj SQLMetal ke generování souboru kódu z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="428c0-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="428c0-146">Další informace najdete v oddílu požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="428c0-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="428c0-147">Chcete-li přidat soubor kódu northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="428c0-147">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="428c0-148">Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="428c0-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="428c0-149">V **přidat existující položku** dialogové okno, přejděte do c:\linqtest6\northwind.cs a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="428c0-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="428c0-150">Soubor northwind.cs je přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="428c0-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="428c0-151">Nastavení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="428c0-151">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="428c0-152">Nejprve zkontrolujte připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="428c0-152">First, test your connection to the database.</span></span> <span data-ttu-id="428c0-153">Zejména Všimněte si, že databáze, Northwnd, nemá žádné i znak.</span><span class="sxs-lookup"><span data-stu-id="428c0-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="428c0-154">Pokud se generují chyby v dalších krocích, zkontrolujte soubor northwind.cs k určení, jak je napsaný částečné třídy Northwind.</span><span class="sxs-lookup"><span data-stu-id="428c0-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="428c0-155">K nastavení a otestovat připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="428c0-155">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="428c0-156">Zadejte nebo vložte následující kód do `Main` metodu do třídy Program:</span><span class="sxs-lookup"><span data-stu-id="428c0-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  <span data-ttu-id="428c0-157">Testování aplikace v tomto okamžiku stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="428c0-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="428c0-158">A **konzoly** otevře se okno.</span><span class="sxs-lookup"><span data-stu-id="428c0-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="428c0-159">Aplikace můžete zavřít stisknutím klávesy Enter v **konzoly** okna, nebo kliknutím **Zastavit ladění** v sadě Visual Studio **ladění** nabídky.</span><span class="sxs-lookup"><span data-stu-id="428c0-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="428c0-160">Vytvoření nové Entity</span><span class="sxs-lookup"><span data-stu-id="428c0-160">Creating a New Entity</span></span>  
 <span data-ttu-id="428c0-161">Vytvoření nové entity je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="428c0-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="428c0-162">Můžete vytvořit objekty (například `Customer`) s použitím `new` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="428c0-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="428c0-163">V této a v dalších částech provádíte změny pouze do místní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="428c0-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="428c0-164">Žádné změny se odesílají do databáze až do okamžiku volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na konci tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="428c0-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="428c0-165">Chcete-li přidat nový objekt entity zákazníka</span><span class="sxs-lookup"><span data-stu-id="428c0-165">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="428c0-166">Vytvořte nový `Customer` přidáním následujícího kódu před `Console.ReadLine();` v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="428c0-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  <span data-ttu-id="428c0-167">Stiskněte klávesu F5, chcete-li ladit řešení.</span><span class="sxs-lookup"><span data-stu-id="428c0-167">Press F5 to debug the solution.</span></span>  
  
3.  <span data-ttu-id="428c0-168">Stisknutím klávesy Enter v **konzoly** okna Zastavit ladění a pokračovat v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="428c0-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="428c0-169">Aktualizují se Entity</span><span class="sxs-lookup"><span data-stu-id="428c0-169">Updating an Entity</span></span>  
 <span data-ttu-id="428c0-170">V následujících krocích se budou načítat `Customer` objektu a změňte některou z jeho vlastností.</span><span class="sxs-lookup"><span data-stu-id="428c0-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="428c0-171">Chcete-li změnit název zákazníka</span><span class="sxs-lookup"><span data-stu-id="428c0-171">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="428c0-172">Přidejte následující kód nad `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="428c0-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="428c0-173">Odstraňuje se entita</span><span class="sxs-lookup"><span data-stu-id="428c0-173">Deleting an Entity</span></span>  
 <span data-ttu-id="428c0-174">Pomocí stejného objektu zákazníka, můžete odstranit první pořadí.</span><span class="sxs-lookup"><span data-stu-id="428c0-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="428c0-175">Následující kód ukazuje, jak server vztahy mezi řádky a tom, jak můžete z databáze odstranit řádek.</span><span class="sxs-lookup"><span data-stu-id="428c0-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="428c0-176">Přidejte následující kód před `Console.ReadLine` zobrazíte, jak je možné odstranit objekty:</span><span class="sxs-lookup"><span data-stu-id="428c0-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="428c0-177">Odstranit řádek</span><span class="sxs-lookup"><span data-stu-id="428c0-177">To delete a row</span></span>  
  
-   <span data-ttu-id="428c0-178">Následující kód přidejte přímo nad `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="428c0-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="428c0-179">Odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="428c0-179">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="428c0-180">Posledním krokem vyžadovaný pro vytvoření, aktualizaci a odstraňování objektů, je ve skutečnosti odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="428c0-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="428c0-181">Bez tohoto kroku změny jsou pouze místní a nezobrazí se ve výsledcích dotazu.</span><span class="sxs-lookup"><span data-stu-id="428c0-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="428c0-182">K odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="428c0-182">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="428c0-183">Vložte následující kód nad `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="428c0-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="428c0-184">Vložte následující kód (po `SubmitChanges`) zobrazíte před a po účinky odeslání změn:</span><span class="sxs-lookup"><span data-stu-id="428c0-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  <span data-ttu-id="428c0-185">Stiskněte klávesu F5, chcete-li ladit řešení.</span><span class="sxs-lookup"><span data-stu-id="428c0-185">Press F5 to debug the solution.</span></span>  
  
4.  <span data-ttu-id="428c0-186">Stisknutím klávesy Enter v **konzoly** okno zavřít aplikaci.</span><span class="sxs-lookup"><span data-stu-id="428c0-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="428c0-187">Po přidání nového zákazníka, odešlete změny nelze provést toto řešení znovu, jak je.</span><span class="sxs-lookup"><span data-stu-id="428c0-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="428c0-188">Pokud chcete znovu spustit řešení, změňte název zákazníka a ID zákazníka, které mají být přidány.</span><span class="sxs-lookup"><span data-stu-id="428c0-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="428c0-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="428c0-189">See also</span></span>
- [<span data-ttu-id="428c0-190">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="428c0-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
