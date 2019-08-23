---
title: 'Návod: Manipulace s daty (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 9e6039feb68d18ff5ce16b7a0532710d672c296e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946953"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="245c2-102">Návod: Manipulace s daty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="245c2-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>
<span data-ttu-id="245c2-103">Tento návod poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravu a odstranění dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="245c2-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="245c2-104">Budete používat kopii ukázkové databáze Northwind pro přidání zákazníka, změnu názvu zákazníka a odstranění objednávky.</span><span class="sxs-lookup"><span data-stu-id="245c2-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="245c2-105">Tento návod byl napsán pomocí Visual Basic nastavení vývoje.</span><span class="sxs-lookup"><span data-stu-id="245c2-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="245c2-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="245c2-106">Prerequisites</span></span>  
 <span data-ttu-id="245c2-107">Tento návod vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="245c2-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="245c2-108">Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest2).</span><span class="sxs-lookup"><span data-stu-id="245c2-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="245c2-109">Před zahájením tohoto návodu vytvořte tuto složku.</span><span class="sxs-lookup"><span data-stu-id="245c2-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="245c2-110">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="245c2-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="245c2-111">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="245c2-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="245c2-112">Pokyny najdete v tématu [stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="245c2-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="245c2-113">Po stažení databáze zkopírujte soubor northwnd. mdf do složky c:\linqtest2.</span><span class="sxs-lookup"><span data-stu-id="245c2-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
- <span data-ttu-id="245c2-114">Visual Basic soubor kódu vygenerovaný z databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="245c2-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="245c2-115">Tento soubor můžete vygenerovat buď pomocí Návrhář relací objektů, nebo pomocí nástroje SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="245c2-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="245c2-116">Tento návod byl napsán pomocí nástroje SQLMetal s následujícím příkazovým řádkem:</span><span class="sxs-lookup"><span data-stu-id="245c2-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="245c2-117">**SQLMetal/Code: "c:\linqtest2\northwind.vb"/Language: VB "C:\linqtest2\northwnd.mdf"/pluralize**</span><span class="sxs-lookup"><span data-stu-id="245c2-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="245c2-118">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="245c2-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="245c2-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="245c2-119">Overview</span></span>  
 <span data-ttu-id="245c2-120">Tento názorný postup se skládá ze šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="245c2-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="245c2-121">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Vytvoření řešení v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="245c2-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="245c2-122">Do projektu se přidává soubor s kódem databáze.</span><span class="sxs-lookup"><span data-stu-id="245c2-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="245c2-123">Vytváření nového objektu zákazníka</span><span class="sxs-lookup"><span data-stu-id="245c2-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="245c2-124">Změna jména kontaktu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="245c2-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="245c2-125">Odstranění objednávky.</span><span class="sxs-lookup"><span data-stu-id="245c2-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="245c2-126">Odesílají se tyto změny do databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="245c2-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="245c2-127">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="245c2-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="245c2-128">V tomto prvním úkolu vytvoříte řešení sady Visual Studio, které obsahuje nezbytné odkazy pro sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="245c2-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="245c2-129">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="245c2-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="245c2-130">V nabídce **soubor** v aplikaci Visual Studio klikněte na **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="245c2-130">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="245c2-131">V podokně **typy projektů** v dialogovém okně **Nový projekt** klikněte na položku **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="245c2-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="245c2-132">V podokně **šablony** klikněte na **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="245c2-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="245c2-133">Do pole **název** zadejte **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="245c2-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="245c2-134">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="245c2-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="245c2-135">Přidání odkazů a direktiv LINQ</span><span class="sxs-lookup"><span data-stu-id="245c2-135">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="245c2-136">Tento návod používá sestavení, která nemusí být nainstalována ve výchozím nastavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="245c2-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="245c2-137">Pokud `System.Data.Linq` není v projektu uvedena jako odkaz (klikněte na tlačítko **Zobrazit všechny soubory** v **Průzkumník řešení** a rozbalte uzel **odkazy** ), přidejte jej, jak je vysvětleno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="245c2-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="245c2-138">Přidání System. data. Linq</span><span class="sxs-lookup"><span data-stu-id="245c2-138">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="245c2-139">V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="245c2-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="245c2-140">V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="245c2-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="245c2-141">Sestavení je přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="245c2-141">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="245c2-142">V editoru kódu přidejte následující direktivy nad **Module1**:</span><span class="sxs-lookup"><span data-stu-id="245c2-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="245c2-143">Přidání souboru s kódem Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="245c2-143">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="245c2-144">Tyto kroky předpokládají, že jste použili nástroj SQLMetal k vygenerování souboru kódu z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="245c2-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="245c2-145">Další informace najdete v části požadavky výše v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="245c2-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="245c2-146">Přidání souboru s kódem Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="245c2-146">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="245c2-147">V nabídce **projekt** klikněte na položku **Přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="245c2-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="245c2-148">V dialogovém okně **Přidat existující položku** přejděte na c:\linqtest2\northwind.vb a pak klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="245c2-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="245c2-149">Do projektu se přidá soubor Northwind. vb.</span><span class="sxs-lookup"><span data-stu-id="245c2-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="245c2-150">Nastavení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="245c2-150">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="245c2-151">Nejprve otestujte připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="245c2-151">First, test your connection to the database.</span></span> <span data-ttu-id="245c2-152">Pamatujte na to, že název databáze northwnd nemá žádný znak.</span><span class="sxs-lookup"><span data-stu-id="245c2-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="245c2-153">Pokud generujete chyby v dalších krocích, zkontrolujte soubor Northwind. vb a určete, jak je částečná třída Northwind napsaná.</span><span class="sxs-lookup"><span data-stu-id="245c2-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="245c2-154">Nastavení a otestování připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="245c2-154">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="245c2-155">Do `Sub Main`následujícího pole zadejte nebo vložte následující kód:</span><span class="sxs-lookup"><span data-stu-id="245c2-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. <span data-ttu-id="245c2-156">V tomto okamžiku otestujte aplikaci stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="245c2-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="245c2-157">Otevře se okno **konzoly** .</span><span class="sxs-lookup"><span data-stu-id="245c2-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="245c2-158">Ukončete aplikaci stisknutím klávesy ENTER v okně **konzoly** nebo kliknutím na **Zastavit ladění** v nabídce **ladění** sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="245c2-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="245c2-159">Vytvoření nové entity</span><span class="sxs-lookup"><span data-stu-id="245c2-159">Creating a New Entity</span></span>  
 <span data-ttu-id="245c2-160">Vytvoření nové entity je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="245c2-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="245c2-161">Můžete vytvořit objekty (například `Customer`) `New` pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="245c2-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="245c2-162">V tomto a v následujících částech provedete změny pouze v místní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="245c2-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="245c2-163">Do databáze se neodesílají žádné změny, dokud nebudete volat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> směrem ke konci tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="245c2-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="245c2-164">Přidání nového objektu entity zákazníka</span><span class="sxs-lookup"><span data-stu-id="245c2-164">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="245c2-165">Vytvořte nový `Customer` přidáním následujícího `Console.ReadLine` kódu do `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="245c2-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="245c2-166">Pro ladění řešení stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="245c2-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="245c2-167">Výsledky, které se zobrazují v okně konzoly, jsou následující:</span><span class="sxs-lookup"><span data-stu-id="245c2-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="245c2-168">Všimněte si, že se nový řádek ve výsledcích nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="245c2-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="245c2-169">Nová data nebyla dosud odeslána do databáze.</span><span class="sxs-lookup"><span data-stu-id="245c2-169">The new data has not yet been submitted to the database.</span></span>  
  
3. <span data-ttu-id="245c2-170">V okně **konzoly** stiskněte klávesu ENTER a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="245c2-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="245c2-171">Aktualizace entity</span><span class="sxs-lookup"><span data-stu-id="245c2-171">Updating an Entity</span></span>  
 <span data-ttu-id="245c2-172">V následujících krocích `Customer` navedete objekt a upravíte jednu z jeho vlastností.</span><span class="sxs-lookup"><span data-stu-id="245c2-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="245c2-173">Změna názvu zákazníka</span><span class="sxs-lookup"><span data-stu-id="245c2-173">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="245c2-174">Níže přidejte následující kód `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="245c2-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="245c2-175">Odstranění entity</span><span class="sxs-lookup"><span data-stu-id="245c2-175">Deleting an Entity</span></span>  
 <span data-ttu-id="245c2-176">Pomocí stejného objektu zákazníka můžete odstranit první objednávku.</span><span class="sxs-lookup"><span data-stu-id="245c2-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="245c2-177">Následující kód ukazuje, jak se mají mezi řádky vymezit servery a jak odstranit řádek z databáze.</span><span class="sxs-lookup"><span data-stu-id="245c2-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="245c2-178">Odstranění řádku</span><span class="sxs-lookup"><span data-stu-id="245c2-178">To delete a row</span></span>  
  
- <span data-ttu-id="245c2-179">Přidejte následující kód, který je `Console.ReadLine()`právě uveden výše:</span><span class="sxs-lookup"><span data-stu-id="245c2-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="245c2-180">Odesílání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="245c2-180">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="245c2-181">Poslední krok potřebný k vytváření, aktualizaci a odstraňování objektů slouží ke skutečnému odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="245c2-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="245c2-182">Bez tohoto kroku budou vaše změny jenom místní a ve výsledcích dotazu se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="245c2-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="245c2-183">Odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="245c2-183">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="245c2-184">Vložte následující kód hned `Console.ReadLine`takto:</span><span class="sxs-lookup"><span data-stu-id="245c2-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="245c2-185">Vložte následující kód (po `SubmitChanges`), chcete-li zobrazit před a za následky odeslání změn:</span><span class="sxs-lookup"><span data-stu-id="245c2-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. <span data-ttu-id="245c2-186">Pro ladění řešení stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="245c2-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="245c2-187">Okno konzoly se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="245c2-187">The console window appears as follows:</span></span>  
  
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
  
4. <span data-ttu-id="245c2-188">V okně **konzoly** stiskněte klávesu ENTER a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="245c2-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="245c2-189">Po přidání nového zákazníka odesláním změn už toto řešení nemůžete znovu spustit tak, jak je, protože nemůžete přidat stejného zákazníka tak, jak je.</span><span class="sxs-lookup"><span data-stu-id="245c2-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="245c2-190">Pokud chcete řešení znovu spustit, změňte hodnotu ID zákazníka, která se má přidat.</span><span class="sxs-lookup"><span data-stu-id="245c2-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="245c2-191">Viz také:</span><span class="sxs-lookup"><span data-stu-id="245c2-191">See also</span></span>

- [<span data-ttu-id="245c2-192">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="245c2-192">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
