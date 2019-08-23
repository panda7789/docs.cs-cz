---
title: 'Návod: Použití jen uložených procedur (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 159b65b4b58b9142a168401ea2a881af2714df5f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946630"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="9e0ee-102">Návod: Použití jen uložených procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e0ee-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="9e0ee-103">Tento návod poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům pouze pomocí uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="9e0ee-104">Tento přístup často používají správci databáze k omezení způsobu přístupu k úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e0ee-105">Uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacích můžete použít také k přepsání výchozího chování, zejména pro `Create`procesy, `Update`a `Delete` .</span><span class="sxs-lookup"><span data-stu-id="9e0ee-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="9e0ee-106">Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9e0ee-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="9e0ee-107">Pro účely tohoto Názorného postupu použijete dvě metody, které byly namapovány na uložené procedury v ukázkové databázi Northwind: CustOrdersDetail a CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="9e0ee-108">Mapování probíhá při spuštění nástroje příkazového řádku SqlMetal pro vygenerování souboru Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-108">The mapping occurs when you run the SqlMetal command-line tool to generate a Visual Basic file.</span></span> <span data-ttu-id="9e0ee-109">Další informace najdete v části požadavky dále v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="9e0ee-110">Tento návod nespoléhá na Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-110">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="9e0ee-111">Vývojáři, kteří používají Visual Studio, mohou také použít návrháře O/R k implementaci funkcí uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-111">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="9e0ee-112">Viz [nástroje LINQ to SQL v aplikaci Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="9e0ee-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="9e0ee-113">Tento návod byl napsán pomocí Visual Basic nastavení vývoje.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9e0ee-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e0ee-114">Prerequisites</span></span>  
 <span data-ttu-id="9e0ee-115">Tento návod vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-115">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="9e0ee-116">Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest3).</span><span class="sxs-lookup"><span data-stu-id="9e0ee-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="9e0ee-117">Před zahájením tohoto návodu vytvořte tuto složku.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-117">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="9e0ee-118">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="9e0ee-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="9e0ee-119">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="9e0ee-120">Pokyny najdete v tématu [stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="9e0ee-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="9e0ee-121">Po stažení databáze zkopírujte soubor northwnd. mdf do složky c:\linqtest3.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
- <span data-ttu-id="9e0ee-122">Visual Basic soubor kódu vygenerovaný z databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-122">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="9e0ee-123">Tento návod byl napsán pomocí nástroje SqlMetal s následujícím příkazovým řádkem:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="9e0ee-124">**SQLMetal/Code: "c:\linqtest3\northwind.vb"/Language: VB "c:\linqtest3\northwnd.mdf"/sprocs/Functions/pluralize**</span><span class="sxs-lookup"><span data-stu-id="9e0ee-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="9e0ee-125">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="9e0ee-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="9e0ee-126">Přehled</span><span class="sxs-lookup"><span data-stu-id="9e0ee-126">Overview</span></span>  
 <span data-ttu-id="9e0ee-127">Tento názorný postup se skládá ze šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-127">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="9e0ee-128">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Nastavení řešení v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="9e0ee-129">Do projektu se přidává sestavení System. data. Linq.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
- <span data-ttu-id="9e0ee-130">Do projektu se přidává soubor s kódem databáze.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-130">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="9e0ee-131">Vytváří se připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-131">Creating a connection to the database.</span></span>  
  
- <span data-ttu-id="9e0ee-132">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e0ee-132">Setting up the user interface.</span></span>  
  
- <span data-ttu-id="9e0ee-133">Spuštění a testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="9e0ee-134">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9e0ee-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="9e0ee-135">V tomto prvním úkolu vytvoříte řešení sady Visual Studio, které obsahuje nezbytné odkazy pro sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="9e0ee-136">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9e0ee-136">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="9e0ee-137">V nabídce **soubor** v aplikaci Visual Studio klikněte na **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-137">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="9e0ee-138">V podokně **typy projektů** v dialogovém okně **Nový projekt** rozbalte položku **Visual Basic**a potom klikněte na možnost **Windows**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3. <span data-ttu-id="9e0ee-139">V podokně **šablony** klikněte na **model Windows Forms aplikace**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="9e0ee-140">Do pole **název** zadejte **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="9e0ee-141">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="9e0ee-142">Otevře se Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="9e0ee-143">Přidání odkazu na sestavení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9e0ee-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="9e0ee-144">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není zahrnuto do šablony standardní model Windows Forms aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="9e0ee-145">Sestavení bude nutné přidat sami, jak je vysvětleno v následujících krocích:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="9e0ee-146">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="9e0ee-146">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="9e0ee-147">V **Průzkumník řešení**klikněte na **Zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2. <span data-ttu-id="9e0ee-148">V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3. <span data-ttu-id="9e0ee-149">V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="9e0ee-150">Sestavení je přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="9e0ee-151">Přidání souboru s kódem Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="9e0ee-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="9e0ee-152">Tento krok předpokládá, že jste použili nástroj SqlMetal k vygenerování souboru kódu z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="9e0ee-153">Další informace najdete v části požadavky výše v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="9e0ee-154">Přidání souboru s kódem Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="9e0ee-154">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="9e0ee-155">V nabídce **projekt** klikněte na položku **Přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="9e0ee-156">V dialogovém okně **Přidat existující položku** přejděte na c:\linqtest3\northwind.vb a pak klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="9e0ee-157">Do projektu se přidá soubor Northwind. vb.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="9e0ee-158">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="9e0ee-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="9e0ee-159">V tomto kroku nadefinujete připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="9e0ee-160">Tento návod používá jako cestu "c:\linqtest3\northwnd.mdf".</span><span class="sxs-lookup"><span data-stu-id="9e0ee-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
### <a name="to-create-the-database-connection"></a><span data-ttu-id="9e0ee-161">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="9e0ee-161">To create the database connection</span></span>  
  
1. <span data-ttu-id="9e0ee-162">V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1. vb**a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="9e0ee-163">`Class Form1`zobrazí se v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-163">`Class Form1` appears in the code editor.</span></span>  
  
2. <span data-ttu-id="9e0ee-164">Do `Form1` bloku kódu zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="9e0ee-165">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e0ee-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="9e0ee-166">V tomto úkolu vytvoříte rozhraní, aby uživatelé mohli spouštět uložené procedury pro přístup k datům v databázi.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="9e0ee-167">V aplikaci, kterou vyvíjíte pomocí tohoto Názorného postupu, mohou uživatelé získat přístup k datům v databázi pouze pomocí uložených procedur integrovaných v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="9e0ee-168">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e0ee-168">To set up the user interface</span></span>  
  
1. <span data-ttu-id="9e0ee-169">Vraťte se do Návrhář formulářů (**Form1. vb [Design]** ).</span><span class="sxs-lookup"><span data-stu-id="9e0ee-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2. <span data-ttu-id="9e0ee-170">V nabídce **zobrazení** klikněte na příkaz **Sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="9e0ee-171">Otevře se panel nástrojů.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9e0ee-172">Klikněte na ikonu Automatické **skrývání** , aby se panel nástrojů otevřel při provádění zbývajících kroků v této části.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="9e0ee-173">Přetáhněte dvě tlačítka, dvě textová pole a dva popisky z panelu nástrojů na **Form1**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="9e0ee-174">Uspořádejte ovládací prvky jako v doprovodné ilustraci.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="9e0ee-175">Rozbalte **Form1** , aby se ovládací prvky vešly do jednoduchého umístění.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="9e0ee-176">Klikněte pravým tlačítkem na **Label1**a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="9e0ee-177">Změňte vlastnost **text** z **Label1** na **ENTER ČísloObjednávky:** .</span><span class="sxs-lookup"><span data-stu-id="9e0ee-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="9e0ee-178">Stejným způsobem jako u **Label2**změňte vlastnost **text** z **Label2** na **ENTER CustomerID:** .</span><span class="sxs-lookup"><span data-stu-id="9e0ee-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="9e0ee-179">Stejným způsobem změňte vlastnost **text** pro **Button1** na **Podrobnosti objednávky**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="9e0ee-180">Změňte vlastnost **text** pro **Button2** na **Seřadit historii**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="9e0ee-181">Rozšiřte ovládací prvky tlačítko tak, aby byl veškerý text viditelný.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-181">Widen the button controls so that all the text is visible.</span></span>  
  
### <a name="to-handle-button-clicks"></a><span data-ttu-id="9e0ee-182">Pro zpracování kliknutí na tlačítko</span><span class="sxs-lookup"><span data-stu-id="9e0ee-182">To handle button clicks</span></span>  
  
1. <span data-ttu-id="9e0ee-183">Poklikejte na **Podrobnosti objednávky** na **Form1** a vytvořte `Button1` obslužnou rutinu události a otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2. <span data-ttu-id="9e0ee-184">Do `Button1` obslužné rutiny zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. <span data-ttu-id="9e0ee-185">Nyní dvakrát klikněte na **Button2** na Form1 a vytvořte `Button2` obslužnou rutinu události a otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4. <span data-ttu-id="9e0ee-186">Do `Button2` obslužné rutiny zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="9e0ee-187">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="9e0ee-187">Testing the Application</span></span>  
 <span data-ttu-id="9e0ee-188">Nyní je čas testovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-188">Now it is time to test your application.</span></span> <span data-ttu-id="9e0ee-189">Všimněte si, že váš kontakt s úložištěm dat je omezený na jakékoli akce, které můžou tyto dvě uložené procedury provádět.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="9e0ee-190">Tyto akce mají vracet produkty zahrnuté do každé položky ČísloObjednávky, které zadáte, nebo vrátí historii produktů seřazených podle ID zákazníka, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="9e0ee-191">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="9e0ee-191">To test the application</span></span>  
  
1. <span data-ttu-id="9e0ee-192">Stisknutím klávesy F5 spusťte ladění.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="9e0ee-193">Zobrazí se Form1.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-193">Form1 appears.</span></span>  
  
2. <span data-ttu-id="9e0ee-194">Do pole **Zadejte ČísloObjednávky** zadejte **10249** a potom klikněte na **Seřadit podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="9e0ee-195">Okno se zprávou obsahuje seznam produktů obsažených v pořadí 10249.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="9e0ee-196">Kliknutím na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-196">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="9e0ee-197">Do pole **Zadejte CustomerID** zadejte `ALFKI`a pak klikněte na **Historie objednávek**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="9e0ee-198">V okně se zprávou je uveden seznam historie objednávek pro zákaznickou ALFKI.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="9e0ee-199">Kliknutím na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-199">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="9e0ee-200">Do pole **Zadejte ČísloObjednávky** zadejte `123`a potom klikněte na **Seřadit podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="9e0ee-201">Okno se zprávou zobrazí "žádné výsledky".</span><span class="sxs-lookup"><span data-stu-id="9e0ee-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="9e0ee-202">Kliknutím na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-202">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="9e0ee-203">V nabídce **ladění** klikněte na položku **Zastavit ladění**.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="9e0ee-204">Ladicí relace se zavře.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-204">The debug session closes.</span></span>  
  
6. <span data-ttu-id="9e0ee-205">Pokud jste dokončili experimentování, můžete kliknout na **Zavřít projekt** v nabídce **soubor** a po zobrazení výzvy projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9e0ee-206">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9e0ee-206">Next Steps</span></span>  
 <span data-ttu-id="9e0ee-207">Tento projekt můžete vylepšit tím, že provedete nějaké změny.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="9e0ee-208">Můžete například zobrazit seznam dostupných uložených procedur v seznamu a nechat uživatele vybrat, které procedury provést.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="9e0ee-209">Výstup sestav můžete také streamovat do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0ee-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-210">See also</span></span>

- [<span data-ttu-id="9e0ee-211">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="9e0ee-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="9e0ee-212">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="9e0ee-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
