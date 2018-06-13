---
title: 'Návod: Manipulace s daty (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: e0bf8b32595f656d3bff424610f193bd84d0f5bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361650"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="e743c-102">Návod: Manipulace s daty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e743c-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>
<span data-ttu-id="e743c-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravy a odstraňování dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="e743c-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="e743c-104">Kopie v ukázkové databázi Northwind použije k přidání zákazníka, změňte název zákazníka a odstranění objednávky.</span><span class="sxs-lookup"><span data-stu-id="e743c-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="e743c-105">Tento názorný postup napsané pomocí jazyka Visual Basic – vývojové nastavení.</span><span class="sxs-lookup"><span data-stu-id="e743c-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e743c-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e743c-106">Prerequisites</span></span>  
 <span data-ttu-id="e743c-107">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="e743c-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="e743c-108">Tento návod používá k uložení souborů vyhrazené složky ("c:\linqtest2").</span><span class="sxs-lookup"><span data-stu-id="e743c-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="e743c-109">Než začnete návodu, vytvořte této složky.</span><span class="sxs-lookup"><span data-stu-id="e743c-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="e743c-110">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="e743c-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="e743c-111">Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="e743c-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="e743c-112">Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="e743c-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="e743c-113">Po stažení databázi, zkopírujte soubor northwnd.mdf ke složce c:\linqtest2.</span><span class="sxs-lookup"><span data-stu-id="e743c-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
-   <span data-ttu-id="e743c-114">Kód jazyka Visual Basic soubor generovaný z databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="e743c-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="e743c-115">Tento soubor můžete vygenerovat pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo na SQLMetal nástroj.</span><span class="sxs-lookup"><span data-stu-id="e743c-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="e743c-116">Tento názorný postup byla zapsána pomocí nástroje SQLMetal s následující příkazový řádek:</span><span class="sxs-lookup"><span data-stu-id="e743c-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="e743c-117">**SqlMetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" / pluralizovat**</span><span class="sxs-lookup"><span data-stu-id="e743c-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="e743c-118">Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e743c-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e743c-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="e743c-119">Overview</span></span>  
 <span data-ttu-id="e743c-120">Tento názorný postup se skládá z šesti hlavní úlohy:</span><span class="sxs-lookup"><span data-stu-id="e743c-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="e743c-121">Vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e743c-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="e743c-122">Přidání souboru kódu databáze do projektu.</span><span class="sxs-lookup"><span data-stu-id="e743c-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="e743c-123">Vytvoření nového objektu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="e743c-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="e743c-124">Úpravy jméno kontaktní osoby zákazníka.</span><span class="sxs-lookup"><span data-stu-id="e743c-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="e743c-125">Odstranění pořadí.</span><span class="sxs-lookup"><span data-stu-id="e743c-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="e743c-126">Odesílá se tyto změny v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="e743c-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="e743c-127">Vytváření dotazu LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="e743c-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="e743c-128">V této úloze první vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="e743c-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="e743c-129">Chcete-li vytvořit LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="e743c-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="e743c-130">V sadě Visual Studio **soubor** nabídky, klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e743c-130">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="e743c-131">V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **jazyka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="e743c-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3.  <span data-ttu-id="e743c-132">V **šablony** podokně klikněte na tlačítko **konzolové aplikace**.</span><span class="sxs-lookup"><span data-stu-id="e743c-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="e743c-133">V **název** zadejte **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="e743c-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="e743c-134">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="e743c-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="e743c-135">Přidání odkazů LINQ a direktivy</span><span class="sxs-lookup"><span data-stu-id="e743c-135">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="e743c-136">Tento návod používá sestavení, které nemusí být nainstalovány ve výchozím nastavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="e743c-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="e743c-137">Pokud `System.Data.Linq` není uvedena jako odkaz ve vašem projektu (klikněte na tlačítko **zobrazit všechny soubory** v **Průzkumníku řešení** a rozbalte **odkazy** uzlu), přidat, jak je popsáno v Následující kroky.</span><span class="sxs-lookup"><span data-stu-id="e743c-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="e743c-138">Chcete-li přidat System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="e743c-138">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="e743c-139">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="e743c-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="e743c-140">V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="e743c-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e743c-141">Je sestavení přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="e743c-141">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="e743c-142">V editoru kódu, přidejte následující direktivy výše **modul 1**:</span><span class="sxs-lookup"><span data-stu-id="e743c-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e743c-143">Přidání souboru Northwind kódu do projektu</span><span class="sxs-lookup"><span data-stu-id="e743c-143">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="e743c-144">Tento postup předpokládá, že jste použili nástroj SQLMetal generování souboru kódu na základě ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="e743c-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="e743c-145">Další informace najdete v části požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="e743c-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e743c-146">Přidání souboru northwind kódu do projektu</span><span class="sxs-lookup"><span data-stu-id="e743c-146">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="e743c-147">Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="e743c-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="e743c-148">V **přidat existující položku** dialogové okno, přejděte na c:\linqtest2\northwind.vb a pak klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="e743c-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="e743c-149">Soubor northwind.vb je přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="e743c-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="e743c-150">Nastavení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="e743c-150">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="e743c-151">Nejprve zkontrolujte připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="e743c-151">First, test your connection to the database.</span></span> <span data-ttu-id="e743c-152">Zejména Všimněte si, že název databáze, Northwnd, nemá žádné i znak.</span><span class="sxs-lookup"><span data-stu-id="e743c-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="e743c-153">Pokud se v dalších krocích můžete způsobit chyby, zkontrolujte soubor northwind.vb k určení, jak je napsaný Northwind třídu.</span><span class="sxs-lookup"><span data-stu-id="e743c-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="e743c-154">Jak nastavit a otestovat připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="e743c-154">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="e743c-155">Zadejte nebo vložte následující kód do `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="e743c-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  <span data-ttu-id="e743c-156">Stisknutím klávesy F5 testování aplikace v tomto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="e743c-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="e743c-157">A **konzoly** otevře se okno.</span><span class="sxs-lookup"><span data-stu-id="e743c-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="e743c-158">Zavřete aplikaci stisknutím klávesy Enter v **konzoly** okno, nebo kliknutím **Zastavte ladění** v sadě Visual Studio **ladění** nabídky.</span><span class="sxs-lookup"><span data-stu-id="e743c-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="e743c-159">Vytvoření nové Entity</span><span class="sxs-lookup"><span data-stu-id="e743c-159">Creating a New Entity</span></span>  
 <span data-ttu-id="e743c-160">Vytvoření nové entity je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="e743c-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="e743c-161">Můžete vytvořit objekty (například `Customer`) pomocí `New` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e743c-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="e743c-162">V této a v následujících částech provádíte změny pouze do místní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e743c-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="e743c-163">Žádné změny se odesílají do databáze, dokud zavoláte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na konci tohoto průvodce.</span><span class="sxs-lookup"><span data-stu-id="e743c-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="e743c-164">Chcete-li přidat nový objekt entity zákazníka</span><span class="sxs-lookup"><span data-stu-id="e743c-164">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="e743c-165">Vytvořte novou `Customer` přidáním následujícího kódu před `Console.ReadLine` v `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="e743c-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="e743c-166">Stisknutím klávesy F5 ladění řešení.</span><span class="sxs-lookup"><span data-stu-id="e743c-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="e743c-167">Výsledky, které jsou zobrazeny v okně konzoly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="e743c-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="e743c-168">Všimněte si, že nový řádek nezobrazí ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="e743c-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="e743c-169">Nová data do databáze dosud nebyla odeslána.</span><span class="sxs-lookup"><span data-stu-id="e743c-169">The new data has not yet been submitted to the database.</span></span>  
  
3.  <span data-ttu-id="e743c-170">Stiskněte klávesu Enter v **konzoly** okno přestane ladění.</span><span class="sxs-lookup"><span data-stu-id="e743c-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="e743c-171">Aktualizace Entity</span><span class="sxs-lookup"><span data-stu-id="e743c-171">Updating an Entity</span></span>  
 <span data-ttu-id="e743c-172">V následujících krocích se budou načítat `Customer` objekt a upravte jednu ze svých vlastností.</span><span class="sxs-lookup"><span data-stu-id="e743c-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="e743c-173">Chcete-li změnit název zákazníka</span><span class="sxs-lookup"><span data-stu-id="e743c-173">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="e743c-174">Přidejte následující kód výše `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="e743c-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="e743c-175">Odstranění Entity</span><span class="sxs-lookup"><span data-stu-id="e743c-175">Deleting an Entity</span></span>  
 <span data-ttu-id="e743c-176">Pomocí stejného objektu zákazníka, můžete odstranit první pořadí.</span><span class="sxs-lookup"><span data-stu-id="e743c-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="e743c-177">Následující kód ukazuje, jak severu vztahy mezi řádky a jak odstranit řádek z databáze.</span><span class="sxs-lookup"><span data-stu-id="e743c-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="e743c-178">Chcete-li odstranit řádek</span><span class="sxs-lookup"><span data-stu-id="e743c-178">To delete a row</span></span>  
  
-   <span data-ttu-id="e743c-179">Přidejte následující kód právě vyšší `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="e743c-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="e743c-180">Odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="e743c-180">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="e743c-181">V posledním kroku potřebné k vytváření, aktualizaci a odstraňování objektů je ve skutečnosti odeslat provedené změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="e743c-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="e743c-182">Bez tohoto kroku změny jsou pouze místní a nezobrazí ve výsledcích dotazů.</span><span class="sxs-lookup"><span data-stu-id="e743c-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="e743c-183">Odeslat změny do databáze</span><span class="sxs-lookup"><span data-stu-id="e743c-183">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="e743c-184">Následující kód nad vložení `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="e743c-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  <span data-ttu-id="e743c-185">Vložte následující kód (po `SubmitChanges`) zobrazíte před a po důsledky odesílání změny:</span><span class="sxs-lookup"><span data-stu-id="e743c-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  <span data-ttu-id="e743c-186">Stisknutím klávesy F5 ladění řešení.</span><span class="sxs-lookup"><span data-stu-id="e743c-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="e743c-187">V okně konzoly zobrazí se následující:</span><span class="sxs-lookup"><span data-stu-id="e743c-187">The console window appears as follows:</span></span>  
  
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
  
4.  <span data-ttu-id="e743c-188">Stiskněte klávesu Enter v **konzoly** okno přestane ladění.</span><span class="sxs-lookup"><span data-stu-id="e743c-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e743c-189">Po přidání nového zákazníka odesláním změny, nelze provést toto řešení znovu, protože nelze přidat tentýž zákazník znovu jako je.</span><span class="sxs-lookup"><span data-stu-id="e743c-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="e743c-190">Znovu provést řešení, změňte hodnotu ID zákazníka, které chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="e743c-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e743c-191">Viz také</span><span class="sxs-lookup"><span data-stu-id="e743c-191">See Also</span></span>  
 [<span data-ttu-id="e743c-192">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="e743c-192">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
