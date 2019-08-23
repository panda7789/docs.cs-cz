---
title: 'Návod: Manipulace s daty (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: 7921f0aa7582e70967f7fec633f37ef0dbc766de
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946977"
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="300c8-102">Návod: Manipulace s daty (C#)</span><span class="sxs-lookup"><span data-stu-id="300c8-102">Walkthrough: Manipulating Data (C#)</span></span>
<span data-ttu-id="300c8-103">Tento návod poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravu a odstranění dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="300c8-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="300c8-104">Budete používat kopii ukázkové databáze Northwind pro přidání zákazníka, změnu názvu zákazníka a odstranění objednávky.</span><span class="sxs-lookup"><span data-stu-id="300c8-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="300c8-105">Tento návod byl napsán s použitím nastavení C# vizuálního vývoje.</span><span class="sxs-lookup"><span data-stu-id="300c8-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="300c8-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="300c8-106">Prerequisites</span></span>  
 <span data-ttu-id="300c8-107">Tento návod vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="300c8-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="300c8-108">Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest6).</span><span class="sxs-lookup"><span data-stu-id="300c8-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="300c8-109">Před zahájením tohoto návodu vytvořte tuto složku.</span><span class="sxs-lookup"><span data-stu-id="300c8-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="300c8-110">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="300c8-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="300c8-111">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="300c8-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="300c8-112">Pokyny najdete v tématu [stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="300c8-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="300c8-113">Po stažení databáze zkopírujte soubor northwnd. mdf do složky c:\linqtest6.</span><span class="sxs-lookup"><span data-stu-id="300c8-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
- <span data-ttu-id="300c8-114">Soubor C# kódu vygenerovaný z databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="300c8-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="300c8-115">Tento soubor můžete vygenerovat buď pomocí Návrhář relací objektů, nebo pomocí nástroje SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="300c8-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="300c8-116">Tento návod byl napsán pomocí nástroje SQLMetal s následujícím příkazovým řádkem:</span><span class="sxs-lookup"><span data-stu-id="300c8-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="300c8-117">**SQLMetal/Code: "c:\linqtest6\northwind.cs"/Language: CSharp "C:\linqtest6\northwnd.mdf"/pluralize**</span><span class="sxs-lookup"><span data-stu-id="300c8-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="300c8-118">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="300c8-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="300c8-119">Přehled</span><span class="sxs-lookup"><span data-stu-id="300c8-119">Overview</span></span>  
 <span data-ttu-id="300c8-120">Tento názorný postup se skládá ze šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="300c8-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="300c8-121">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Vytvoření řešení v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="300c8-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="300c8-122">Do projektu se přidává soubor s kódem databáze.</span><span class="sxs-lookup"><span data-stu-id="300c8-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="300c8-123">Vytváření nového objektu zákazníka</span><span class="sxs-lookup"><span data-stu-id="300c8-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="300c8-124">Změna jména kontaktu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="300c8-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="300c8-125">Odstranění objednávky.</span><span class="sxs-lookup"><span data-stu-id="300c8-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="300c8-126">Odesílají se tyto změny do databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="300c8-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="300c8-127">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="300c8-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="300c8-128">V tomto prvním úkolu vytvoříte řešení sady Visual Studio, které obsahuje nezbytné odkazy pro sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="300c8-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="300c8-129">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="300c8-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="300c8-130">V nabídce **soubor** v aplikaci Visual Studio přejděte na **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="300c8-130">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="300c8-131">V podokně **typy projektů** v dialogovém okně **Nový projekt** klikněte na položku **vizuál C#** .</span><span class="sxs-lookup"><span data-stu-id="300c8-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="300c8-132">V podokně **šablony** klikněte na **Konzolová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="300c8-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="300c8-133">Do pole **název** zadejte **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="300c8-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="300c8-134">V poli **umístění** ověřte, kam chcete uložit soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="300c8-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="300c8-135">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="300c8-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="300c8-136">Přidání odkazů a direktiv LINQ</span><span class="sxs-lookup"><span data-stu-id="300c8-136">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="300c8-137">Tento návod používá sestavení, která nemusí být nainstalována ve výchozím nastavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="300c8-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="300c8-138">Pokud System. data. Linq není v projektu uveden jako odkaz, přidejte jej, jak je vysvětleno v následujícím postupu:</span><span class="sxs-lookup"><span data-stu-id="300c8-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="300c8-139">Přidání System. data. Linq</span><span class="sxs-lookup"><span data-stu-id="300c8-139">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="300c8-140">V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="300c8-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="300c8-141">V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="300c8-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="300c8-142">Sestavení je přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="300c8-142">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="300c8-143">Do horní části Program.cs přidejte následující direktivy:</span><span class="sxs-lookup"><span data-stu-id="300c8-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="300c8-144">Přidání souboru s kódem Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="300c8-144">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="300c8-145">Tyto kroky předpokládají, že jste použili nástroj SQLMetal k vygenerování souboru kódu z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="300c8-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="300c8-146">Další informace najdete v části požadavky výše v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="300c8-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="300c8-147">Přidání souboru s kódem Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="300c8-147">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="300c8-148">V nabídce **projekt** klikněte na položku **Přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="300c8-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="300c8-149">V dialogovém okně **Přidat existující položku** přejděte na c:\linqtest6\northwind.cs a pak klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="300c8-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="300c8-150">Soubor northwind.cs se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="300c8-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="300c8-151">Nastavení připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="300c8-151">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="300c8-152">Nejprve otestujte připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="300c8-152">First, test your connection to the database.</span></span> <span data-ttu-id="300c8-153">Pamatujte na to, že databáze northwnd nemá žádný znak.</span><span class="sxs-lookup"><span data-stu-id="300c8-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="300c8-154">Pokud generujete chyby v dalších krocích, zkontrolujte soubor northwind.cs a určete, jak je částečná třída Northwind napsaná.</span><span class="sxs-lookup"><span data-stu-id="300c8-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="300c8-155">Nastavení a otestování připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="300c8-155">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="300c8-156">Zadejte nebo vložte následující kód do `Main` metody ve třídě program:</span><span class="sxs-lookup"><span data-stu-id="300c8-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. <span data-ttu-id="300c8-157">V tomto okamžiku otestujte aplikaci stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="300c8-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="300c8-158">Otevře se okno **konzoly** .</span><span class="sxs-lookup"><span data-stu-id="300c8-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="300c8-159">Aplikaci můžete zavřít stisknutím klávesy ENTER v okně **konzoly** nebo kliknutím na **Zastavit ladění** v nabídce **ladění** aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="300c8-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="300c8-160">Vytvoření nové entity</span><span class="sxs-lookup"><span data-stu-id="300c8-160">Creating a New Entity</span></span>  
 <span data-ttu-id="300c8-161">Vytvoření nové entity je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="300c8-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="300c8-162">Můžete vytvořit objekty (například `Customer`) `new` pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="300c8-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="300c8-163">V tomto a v následujících částech provedete změny pouze v místní mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="300c8-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="300c8-164">Do databáze se neodesílají žádné změny, dokud nebudete volat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> směrem ke konci tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="300c8-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="300c8-165">Přidání nového objektu entity zákazníka</span><span class="sxs-lookup"><span data-stu-id="300c8-165">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="300c8-166">Vytvořte nový `Customer` přidáním následujícího `Console.ReadLine();` kódu do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="300c8-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="300c8-167">Pro ladění řešení stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="300c8-167">Press F5 to debug the solution.</span></span>  
  
3. <span data-ttu-id="300c8-168">V okně **konzoly** stiskněte klávesu ENTER a zastavte ladění a pokračujte v tomto postupu.</span><span class="sxs-lookup"><span data-stu-id="300c8-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="300c8-169">Aktualizace entity</span><span class="sxs-lookup"><span data-stu-id="300c8-169">Updating an Entity</span></span>  
 <span data-ttu-id="300c8-170">V následujících krocích `Customer` navedete objekt a upravíte jednu z jeho vlastností.</span><span class="sxs-lookup"><span data-stu-id="300c8-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="300c8-171">Změna názvu zákazníka</span><span class="sxs-lookup"><span data-stu-id="300c8-171">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="300c8-172">Níže přidejte následující kód `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="300c8-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="300c8-173">Odstranění entity</span><span class="sxs-lookup"><span data-stu-id="300c8-173">Deleting an Entity</span></span>  
 <span data-ttu-id="300c8-174">Pomocí stejného objektu zákazníka můžete odstranit první objednávku.</span><span class="sxs-lookup"><span data-stu-id="300c8-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="300c8-175">Následující kód ukazuje, jak se mají mezi řádky vymezit servery a jak odstranit řádek z databáze.</span><span class="sxs-lookup"><span data-stu-id="300c8-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="300c8-176">`Console.ReadLine` Chcete-li zjistit, jak lze objekty odstranit, přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="300c8-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="300c8-177">Odstranění řádku</span><span class="sxs-lookup"><span data-stu-id="300c8-177">To delete a row</span></span>  
  
- <span data-ttu-id="300c8-178">Přidejte následující kód, který je `Console.ReadLine();`právě uveden výše:</span><span class="sxs-lookup"><span data-stu-id="300c8-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="300c8-179">Odesílání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="300c8-179">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="300c8-180">Poslední krok potřebný k vytváření, aktualizaci a odstraňování objektů slouží ke skutečnému odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="300c8-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="300c8-181">Bez tohoto kroku budou vaše změny jenom místní a ve výsledcích dotazu se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="300c8-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="300c8-182">Odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="300c8-182">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="300c8-183">Vložte následující kód hned `Console.ReadLine`takto:</span><span class="sxs-lookup"><span data-stu-id="300c8-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. <span data-ttu-id="300c8-184">Vložte následující kód (po `SubmitChanges`), chcete-li zobrazit před a za následky odeslání změn:</span><span class="sxs-lookup"><span data-stu-id="300c8-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. <span data-ttu-id="300c8-185">Pro ladění řešení stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="300c8-185">Press F5 to debug the solution.</span></span>  
  
4. <span data-ttu-id="300c8-186">V okně **konzoly** stiskněte klávesu ENTER, aby se aplikace zavřela.</span><span class="sxs-lookup"><span data-stu-id="300c8-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="300c8-187">Po přidání nového zákazníka odesláním změn už toto řešení nebudete moct znovu spustit, jak je.</span><span class="sxs-lookup"><span data-stu-id="300c8-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="300c8-188">Pokud chcete řešení znovu spustit, změňte jméno zákazníka a ID zákazníka, které chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="300c8-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="300c8-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="300c8-189">See also</span></span>

- [<span data-ttu-id="300c8-190">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="300c8-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
