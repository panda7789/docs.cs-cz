---
title: 'Návod: Manipulace s daty (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 27ac9de488a92d838df06d4a501a9148e87b9c9f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742717"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="f763e-102">Návod: Manipulace s daty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f763e-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>
<span data-ttu-id="f763e-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravy a odstraňování dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="f763e-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="f763e-104">Přidejte zákazníka, změňte název zákazníka a odstranit objednávky použijete kopii ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="f763e-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="f763e-105">Tento návod byl napsán s použitím vývojového nastavení jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f763e-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f763e-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f763e-106">Prerequisites</span></span>  
 <span data-ttu-id="f763e-107">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="f763e-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="f763e-108">Tento návod používá vyhrazené složky ("c:\linqtest2") pro uložení souborů.</span><span class="sxs-lookup"><span data-stu-id="f763e-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="f763e-109">Vytvoření této složky, před zahájením návodu.</span><span class="sxs-lookup"><span data-stu-id="f763e-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="f763e-110">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="f763e-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="f763e-111">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="f763e-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="f763e-112">Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="f763e-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="f763e-113">Po stažení databáze, zkopírujte do složky c:\linqtest2 northwnd.mdf souboru.</span><span class="sxs-lookup"><span data-stu-id="f763e-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
- <span data-ttu-id="f763e-114">Soubor kódu jazyka Visual Basic generují z databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="f763e-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="f763e-115">Tento soubor můžete vygenerovat pomocí Návrháře relací objektů nebo nástroji SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="f763e-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="f763e-116">Tento návod byl napsán s použitím nástroje SQLMetal s následujícím příkazovým řádkem:</span><span class="sxs-lookup"><span data-stu-id="f763e-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="f763e-117">**SqlMetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" / pluralize**</span><span class="sxs-lookup"><span data-stu-id="f763e-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="f763e-118">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="f763e-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="f763e-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="f763e-119">Overview</span></span>  
 <span data-ttu-id="f763e-120">Tento názorný postup se skládá z šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="f763e-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="f763e-121">Vytváří [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f763e-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="f763e-122">Přidání kódu databázový soubor do projektu.</span><span class="sxs-lookup"><span data-stu-id="f763e-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="f763e-123">Vytváří se nový objekt zákazníka.</span><span class="sxs-lookup"><span data-stu-id="f763e-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="f763e-124">Úprava kontaktní jméno zákazníka.</span><span class="sxs-lookup"><span data-stu-id="f763e-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="f763e-125">Odstraňuje se objednávky.</span><span class="sxs-lookup"><span data-stu-id="f763e-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="f763e-126">Odesílá se tyto změny k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f763e-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="f763e-127">Vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="f763e-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="f763e-128">V této první úloze vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="f763e-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="f763e-129">K vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="f763e-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="f763e-130">V sadě Visual Studio **souboru** nabídky, klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="f763e-130">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="f763e-131">V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **jazyka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="f763e-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="f763e-132">V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="f763e-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="f763e-133">V **název** zadejte **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="f763e-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="f763e-134">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="f763e-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="f763e-135">Přidání odkazů LINQ a direktivy</span><span class="sxs-lookup"><span data-stu-id="f763e-135">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="f763e-136">Tento návod používá sestavení, která nemusí být nainstalován ve výchozím nastavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="f763e-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="f763e-137">Pokud `System.Data.Linq` není uveden jako odkaz v projektu (klikněte na tlačítko **zobrazit všechny soubory** v **Průzkumníku řešení** a rozbalte **odkazy** uzlu), přidat, jak je vysvětleno v Následující kroky.</span><span class="sxs-lookup"><span data-stu-id="f763e-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="f763e-138">Chcete-li přidat System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="f763e-138">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="f763e-139">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="f763e-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="f763e-140">V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="f763e-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f763e-141">Sestavení se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="f763e-141">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="f763e-142">V editoru kódu přidejte následující direktivy výše **Module1**:</span><span class="sxs-lookup"><span data-stu-id="f763e-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="f763e-143">Přidání souboru Northwind kódu do projektu</span><span class="sxs-lookup"><span data-stu-id="f763e-143">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="f763e-144">Tento postup předpokládá, že jste použili nástroj SQLMetal ke generování souboru kódu z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="f763e-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="f763e-145">Další informace najdete v oddílu požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="f763e-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="f763e-146">Chcete-li přidat soubor kódu northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="f763e-146">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="f763e-147">Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="f763e-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="f763e-148">V **přidat existující položku** dialogové okno, přejděte do c:\linqtest2\northwind.vb a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="f763e-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="f763e-149">Soubor northwind.vb je přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="f763e-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="f763e-150">Nastavení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="f763e-150">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="f763e-151">Nejprve zkontrolujte připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="f763e-151">First, test your connection to the database.</span></span> <span data-ttu-id="f763e-152">Zejména Všimněte si, že název databáze, Northwnd, nemá žádné i znak.</span><span class="sxs-lookup"><span data-stu-id="f763e-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="f763e-153">Pokud se generují chyby v dalších krocích, zkontrolujte soubor northwind.vb k určení, jak je napsaný částečné třídy Northwind.</span><span class="sxs-lookup"><span data-stu-id="f763e-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="f763e-154">K nastavení a otestovat připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="f763e-154">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="f763e-155">Zadejte nebo vložte následující kód do `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="f763e-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. <span data-ttu-id="f763e-156">Testování aplikace v tomto okamžiku stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="f763e-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="f763e-157">A **konzoly** otevře se okno.</span><span class="sxs-lookup"><span data-stu-id="f763e-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="f763e-158">Ukončete aplikaci stisknutím klávesy Enter v **konzoly** okna, nebo kliknutím **Zastavit ladění** v sadě Visual Studio **ladění** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f763e-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="f763e-159">Vytvoření nové Entity</span><span class="sxs-lookup"><span data-stu-id="f763e-159">Creating a New Entity</span></span>  
 <span data-ttu-id="f763e-160">Vytvoření nové entity je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="f763e-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="f763e-161">Můžete vytvořit objekty (například `Customer`) s použitím `New` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f763e-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="f763e-162">V této a v dalších částech provádíte změny pouze do místní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f763e-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="f763e-163">Žádné změny se odesílají do databáze až do okamžiku volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na konci tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="f763e-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="f763e-164">Chcete-li přidat nový objekt entity zákazníka</span><span class="sxs-lookup"><span data-stu-id="f763e-164">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="f763e-165">Vytvořte nový `Customer` přidáním následujícího kódu před `Console.ReadLine` v `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="f763e-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="f763e-166">Stiskněte klávesu F5, chcete-li ladit řešení.</span><span class="sxs-lookup"><span data-stu-id="f763e-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="f763e-167">Výsledky, které jsou zobrazeny v okně konzoly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f763e-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="f763e-168">Všimněte si, že na novém řádku se nezobrazí ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="f763e-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="f763e-169">Nová data dosud nebyla odeslána do databáze.</span><span class="sxs-lookup"><span data-stu-id="f763e-169">The new data has not yet been submitted to the database.</span></span>  
  
3. <span data-ttu-id="f763e-170">Stisknutím klávesy Enter v **konzoly** okno chcete zastavit ladění.</span><span class="sxs-lookup"><span data-stu-id="f763e-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="f763e-171">Aktualizují se Entity</span><span class="sxs-lookup"><span data-stu-id="f763e-171">Updating an Entity</span></span>  
 <span data-ttu-id="f763e-172">V následujících krocích se budou načítat `Customer` objektu a změňte některou z jeho vlastností.</span><span class="sxs-lookup"><span data-stu-id="f763e-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="f763e-173">Chcete-li změnit název zákazníka</span><span class="sxs-lookup"><span data-stu-id="f763e-173">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="f763e-174">Přidejte následující kód nad `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="f763e-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="f763e-175">Odstraňuje se entita</span><span class="sxs-lookup"><span data-stu-id="f763e-175">Deleting an Entity</span></span>  
 <span data-ttu-id="f763e-176">Pomocí stejného objektu zákazníka, můžete odstranit první pořadí.</span><span class="sxs-lookup"><span data-stu-id="f763e-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="f763e-177">Následující kód ukazuje, jak server vztahy mezi řádky a tom, jak můžete z databáze odstranit řádek.</span><span class="sxs-lookup"><span data-stu-id="f763e-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="f763e-178">Odstranit řádek</span><span class="sxs-lookup"><span data-stu-id="f763e-178">To delete a row</span></span>  
  
- <span data-ttu-id="f763e-179">Následující kód přidejte přímo nad `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="f763e-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="f763e-180">Odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="f763e-180">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="f763e-181">Poslední krok vyžadovaný pro vytvoření, aktualizaci a odstraňování objektů je ve skutečnosti odeslat provedené změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="f763e-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="f763e-182">Bez tohoto kroku změny jsou pouze místní a nezobrazí se ve výsledcích dotazu.</span><span class="sxs-lookup"><span data-stu-id="f763e-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="f763e-183">K odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="f763e-183">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="f763e-184">Vložte následující kód nad `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="f763e-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="f763e-185">Vložte následující kód (po `SubmitChanges`) zobrazíte před a po účinky odeslání změn:</span><span class="sxs-lookup"><span data-stu-id="f763e-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. <span data-ttu-id="f763e-186">Stiskněte klávesu F5, chcete-li ladit řešení.</span><span class="sxs-lookup"><span data-stu-id="f763e-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="f763e-187">V okně konzoly se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="f763e-187">The console window appears as follows:</span></span>  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. <span data-ttu-id="f763e-188">Stisknutím klávesy Enter v **konzoly** okno chcete zastavit ladění.</span><span class="sxs-lookup"><span data-stu-id="f763e-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f763e-189">Po přidání nového zákazníka, odešlete změny nelze provést toto řešení znovu, je-li tento parametr, vzhledem k tomu, že nemůžete přidat stejnou zákazníka znovu jako je.</span><span class="sxs-lookup"><span data-stu-id="f763e-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="f763e-190">Pokud chcete znovu spustit řešení, změňte hodnotu ID zákazníka, které mají být přidány.</span><span class="sxs-lookup"><span data-stu-id="f763e-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f763e-191">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f763e-191">See also</span></span>

- [<span data-ttu-id="f763e-192">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="f763e-192">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
