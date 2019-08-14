---
title: 'Návod: Použití jen uložených procedur (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: 69419dd5bb49c2e47315d0079df3a7b575ad9afd
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971767"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="584e6-102">Návod: Použití jen uložených procedur (C#)</span><span class="sxs-lookup"><span data-stu-id="584e6-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>

<span data-ttu-id="584e6-103">Tento názorný postup poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům, a to provedením uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="584e6-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="584e6-104">Tento přístup často používají správci databáze k omezení způsobu přístupu k úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="584e6-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>

> [!NOTE]
> <span data-ttu-id="584e6-105">Uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacích můžete použít také k přepsání výchozího chování, zejména pro `Create`procesy, `Update`a `Delete` .</span><span class="sxs-lookup"><span data-stu-id="584e6-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="584e6-106">Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="584e6-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>

<span data-ttu-id="584e6-107">Pro účely tohoto Názorného postupu použijete dvě metody, které byly namapovány na uložené procedury v ukázkové databázi Northwind: CustOrdersDetail a CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="584e6-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="584e6-108">Mapování probíhá při spuštění nástroje příkazového řádku SqlMetal pro vygenerování C# souboru.</span><span class="sxs-lookup"><span data-stu-id="584e6-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="584e6-109">Další informace najdete v části požadavky dále v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="584e6-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>

<span data-ttu-id="584e6-110">Tento návod nespoléhá na Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="584e6-110">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="584e6-111">Vývojáři, kteří používají Visual Studio, mohou také použít návrháře O/R k implementaci funkcí uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="584e6-111">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="584e6-112">Viz [nástroje LINQ to SQL v aplikaci Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="584e6-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="584e6-113">Tento návod byl napsán s použitím nastavení C# vizuálního vývoje.</span><span class="sxs-lookup"><span data-stu-id="584e6-113">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="584e6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="584e6-114">Prerequisites</span></span>

<span data-ttu-id="584e6-115">Tento návod vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="584e6-115">This walkthrough requires the following:</span></span>

- <span data-ttu-id="584e6-116">Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest7).</span><span class="sxs-lookup"><span data-stu-id="584e6-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="584e6-117">Před zahájením tohoto návodu vytvořte tuto složku.</span><span class="sxs-lookup"><span data-stu-id="584e6-117">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="584e6-118">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="584e6-118">The Northwind sample database.</span></span>

     <span data-ttu-id="584e6-119">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="584e6-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="584e6-120">Pokyny najdete v tématu [stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="584e6-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="584e6-121">Po stažení databáze zkopírujte soubor northwnd. mdf do složky c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="584e6-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>

- <span data-ttu-id="584e6-122">Soubor C# kódu vygenerovaný z databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="584e6-122">A C# code file generated from the Northwind database.</span></span>

     <span data-ttu-id="584e6-123">Tento návod byl napsán pomocí nástroje SqlMetal s následujícím příkazovým řádkem:</span><span class="sxs-lookup"><span data-stu-id="584e6-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>

     <span data-ttu-id="584e6-124">**SQLMetal/Code: "c:\linqtest7\northwind.cs"/Language: CSharp "c:\linqtest7\northwnd.mdf"/sprocs/Functions/pluralize**</span><span class="sxs-lookup"><span data-stu-id="584e6-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>

     <span data-ttu-id="584e6-125">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="584e6-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>

## <a name="overview"></a><span data-ttu-id="584e6-126">Přehled</span><span class="sxs-lookup"><span data-stu-id="584e6-126">Overview</span></span>

<span data-ttu-id="584e6-127">Tento názorný postup se skládá ze šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="584e6-127">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="584e6-128">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Nastavení řešení v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="584e6-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="584e6-129">Do projektu se přidává sestavení System. data. Linq.</span><span class="sxs-lookup"><span data-stu-id="584e6-129">Adding the System.Data.Linq assembly to the project.</span></span>

- <span data-ttu-id="584e6-130">Do projektu se přidává soubor s kódem databáze.</span><span class="sxs-lookup"><span data-stu-id="584e6-130">Adding the database code file to the project.</span></span>

- <span data-ttu-id="584e6-131">Vytváří se připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="584e6-131">Creating a connection with the database.</span></span>

- <span data-ttu-id="584e6-132">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="584e6-132">Setting up the user interface.</span></span>

- <span data-ttu-id="584e6-133">Spuštění a testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="584e6-133">Running and testing the application.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="584e6-134">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="584e6-134">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="584e6-135">V tomto prvním úkolu vytvoříte řešení sady Visual Studio, které obsahuje nezbytné odkazy pro sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="584e6-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="584e6-136">Vytvoření řešení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="584e6-136">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="584e6-137">V nabídce **soubor** v aplikaci Visual Studio přejděte na **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="584e6-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="584e6-138">V podokně **typy projektů** v dialogovém okně **Nový projekt** klikněte na položku **vizuál C#** .</span><span class="sxs-lookup"><span data-stu-id="584e6-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="584e6-139">V podokně **šablony** klikněte na **model Windows Forms aplikace**.</span><span class="sxs-lookup"><span data-stu-id="584e6-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>

4. <span data-ttu-id="584e6-140">Do pole **název** zadejte **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="584e6-140">In the **Name** box, type **SprocOnlyApp**.</span></span>

5. <span data-ttu-id="584e6-141">V poli **umístění** ověřte, kam chcete uložit soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="584e6-141">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="584e6-142">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="584e6-142">Click **OK**.</span></span>

     <span data-ttu-id="584e6-143">Otevře se Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="584e6-143">The Windows Forms Designer opens.</span></span>

## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="584e6-144">Přidání odkazu na sestavení LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="584e6-144">Adding the LINQ to SQL Assembly Reference</span></span>

<span data-ttu-id="584e6-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není zahrnuto do šablony standardní model Windows Forms aplikace.</span><span class="sxs-lookup"><span data-stu-id="584e6-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="584e6-146">Sestavení bude nutné přidat sami, jak je vysvětleno v následujících krocích:</span><span class="sxs-lookup"><span data-stu-id="584e6-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>

### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="584e6-147">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="584e6-147">To add System.Data.Linq.dll</span></span>

1. <span data-ttu-id="584e6-148">V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="584e6-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="584e6-149">V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="584e6-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="584e6-150">Sestavení je přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="584e6-150">The assembly is added to the project.</span></span>

## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="584e6-151">Přidání souboru s kódem Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="584e6-151">Adding the Northwind Code File to the Project</span></span>

<span data-ttu-id="584e6-152">Tento krok předpokládá, že jste použili nástroj SqlMetal k vygenerování souboru kódu z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="584e6-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="584e6-153">Další informace najdete v části požadavky výše v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="584e6-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="584e6-154">Přidání souboru s kódem Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="584e6-154">To add the northwind code file to the project</span></span>

1. <span data-ttu-id="584e6-155">V nabídce **projekt** klikněte na položku **Přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="584e6-155">On the **Project** menu, click **Add Existing Item**.</span></span>

2. <span data-ttu-id="584e6-156">V dialogovém okně **Přidat existující položku** přejděte na c:\linqtest7\northwind.cs a pak klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="584e6-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>

     <span data-ttu-id="584e6-157">Soubor northwind.cs se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="584e6-157">The northwind.cs file is added to the project.</span></span>

## <a name="creating-a-database-connection"></a><span data-ttu-id="584e6-158">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="584e6-158">Creating a Database Connection</span></span>

<span data-ttu-id="584e6-159">V tomto kroku nadefinujete připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="584e6-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="584e6-160">Tento návod používá jako cestu "c:\linqtest7\northwnd.mdf".</span><span class="sxs-lookup"><span data-stu-id="584e6-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>

### <a name="to-create-the-database-connection"></a><span data-ttu-id="584e6-161">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="584e6-161">To create the database connection</span></span>

1. <span data-ttu-id="584e6-162">V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1.cs**a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="584e6-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>

2. <span data-ttu-id="584e6-163">Do `Form1` třídy zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="584e6-163">Type the following code into the `Form1` class:</span></span>

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a><span data-ttu-id="584e6-164">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="584e6-164">Setting up the User Interface</span></span>

<span data-ttu-id="584e6-165">V této úloze nastavíte rozhraní tak, aby uživatelé mohli spouštět uložené procedury pro přístup k datům v databázi.</span><span class="sxs-lookup"><span data-stu-id="584e6-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="584e6-166">V aplikacích, které vyvíjíte pomocí tohoto Názorného postupu, mohou uživatelé získat přístup k datům v databázi pouze pomocí uložených procedur integrovaných v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="584e6-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>

### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="584e6-167">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="584e6-167">To set up the user interface</span></span>

1. <span data-ttu-id="584e6-168">Vraťte se do Návrhář formulářů (**Form1. cs [Design]** ).</span><span class="sxs-lookup"><span data-stu-id="584e6-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>

2. <span data-ttu-id="584e6-169">V nabídce **zobrazení** klikněte na příkaz **Sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="584e6-169">On the **View** menu, click **Toolbox**.</span></span>

     <span data-ttu-id="584e6-170">Otevře se panel nástrojů.</span><span class="sxs-lookup"><span data-stu-id="584e6-170">The toolbox opens.</span></span>

    > [!NOTE]
    > <span data-ttu-id="584e6-171">Klikněte na ikonu Automatické **skrývání** , aby se panel nástrojů otevřel při provádění zbývajících kroků v této části.</span><span class="sxs-lookup"><span data-stu-id="584e6-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>

3. <span data-ttu-id="584e6-172">Přetáhněte dvě tlačítka, dvě textová pole a dva popisky z panelu nástrojů na **Form1**.</span><span class="sxs-lookup"><span data-stu-id="584e6-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>

     <span data-ttu-id="584e6-173">Uspořádejte ovládací prvky jako v doprovodné ilustraci.</span><span class="sxs-lookup"><span data-stu-id="584e6-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="584e6-174">Rozbalte **Form1** , aby se ovládací prvky vešly do jednoduchého umístění.</span><span class="sxs-lookup"><span data-stu-id="584e6-174">Expand **Form1** so that the controls fit easily.</span></span>

4. <span data-ttu-id="584e6-175">Klikněte pravým tlačítkem na **Label1**a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="584e6-175">Right-click **label1**, and then click **Properties**.</span></span>

5. <span data-ttu-id="584e6-176">Změňte vlastnost **text** z **Label1** na **ENTER ČísloObjednávky:** .</span><span class="sxs-lookup"><span data-stu-id="584e6-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>

6. <span data-ttu-id="584e6-177">Stejným způsobem jako u **Label2**změňte vlastnost **text** z **Label2** na **ENTER CustomerID:** .</span><span class="sxs-lookup"><span data-stu-id="584e6-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>

7. <span data-ttu-id="584e6-178">Stejným způsobem změňte vlastnost **text** pro **Button1** na **Podrobnosti objednávky**.</span><span class="sxs-lookup"><span data-stu-id="584e6-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>

8. <span data-ttu-id="584e6-179">Změňte vlastnost **text** pro **Button2** na **Seřadit historii**.</span><span class="sxs-lookup"><span data-stu-id="584e6-179">Change the **Text** property for **button2** to **Order History**.</span></span>

     <span data-ttu-id="584e6-180">Rozšiřte ovládací prvky tlačítko tak, aby byl veškerý text viditelný.</span><span class="sxs-lookup"><span data-stu-id="584e6-180">Widen the button controls so that all the text is visible.</span></span>

### <a name="to-handle-button-clicks"></a><span data-ttu-id="584e6-181">Pro zpracování kliknutí na tlačítko</span><span class="sxs-lookup"><span data-stu-id="584e6-181">To handle button clicks</span></span>

1. <span data-ttu-id="584e6-182">Poklikejte na **Podrobnosti objednávky** na **Form1** a otevřete obslužnou rutinu události Button1 v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="584e6-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>

2. <span data-ttu-id="584e6-183">Do `button1` obslužné rutiny zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="584e6-183">Type the following code into the `button1` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. <span data-ttu-id="584e6-184">Nyní dvakrát klikněte na položku **Button2** na **Form1** `button2` a otevřete obslužnou rutinu</span><span class="sxs-lookup"><span data-stu-id="584e6-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>

4. <span data-ttu-id="584e6-185">Do `button2` obslužné rutiny zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="584e6-185">Type the following code into the `button2` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a><span data-ttu-id="584e6-186">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="584e6-186">Testing the Application</span></span>

<span data-ttu-id="584e6-187">Nyní je čas testovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="584e6-187">Now it is time to test your application.</span></span> <span data-ttu-id="584e6-188">Všimněte si, že váš kontakt s úložištěm dat je omezený na jakékoli akce, které můžou tyto dvě uložené procedury provádět.</span><span class="sxs-lookup"><span data-stu-id="584e6-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="584e6-189">Tyto akce mají vracet produkty zahrnuté do každé položky ČísloObjednávky, které zadáte, nebo vrátí historii produktů seřazených podle ID zákazníka, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="584e6-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>

### <a name="to-test-the-application"></a><span data-ttu-id="584e6-190">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="584e6-190">To test the application</span></span>

1. <span data-ttu-id="584e6-191">Stisknutím klávesy F5 spusťte ladění.</span><span class="sxs-lookup"><span data-stu-id="584e6-191">Press F5 to start debugging.</span></span>

     <span data-ttu-id="584e6-192">Zobrazí se Form1.</span><span class="sxs-lookup"><span data-stu-id="584e6-192">Form1 appears.</span></span>

2. <span data-ttu-id="584e6-193">Do pole **Zadejte ČísloObjednávky** zadejte `10249`a potom klikněte na **Seřadit podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="584e6-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>

     <span data-ttu-id="584e6-194">Okno se zprávou obsahuje seznam produktů obsažených v pořadí 10249.</span><span class="sxs-lookup"><span data-stu-id="584e6-194">A message box lists the products included in order 10249.</span></span>

     <span data-ttu-id="584e6-195">Kliknutím na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="584e6-195">Click **OK** to close the message box.</span></span>

3. <span data-ttu-id="584e6-196">Do pole **Zadejte CustomerID** zadejte `ALFKI`a pak klikněte na **Historie objednávek**.</span><span class="sxs-lookup"><span data-stu-id="584e6-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>

     <span data-ttu-id="584e6-197">Zobrazí se okno se zprávou se seznamem historie objednávek pro zákazníka ALFKI.</span><span class="sxs-lookup"><span data-stu-id="584e6-197">A message box appears that lists the order history for customer ALFKI.</span></span>

     <span data-ttu-id="584e6-198">Kliknutím na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="584e6-198">Click **OK** to close the message box.</span></span>

4. <span data-ttu-id="584e6-199">Do pole **Zadejte ČísloObjednávky** zadejte `123`a potom klikněte na **Seřadit podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="584e6-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>

     <span data-ttu-id="584e6-200">Zobrazí se okno se zprávou bez výsledků.</span><span class="sxs-lookup"><span data-stu-id="584e6-200">A message box appears that displays "No results."</span></span>

     <span data-ttu-id="584e6-201">Kliknutím na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="584e6-201">Click **OK** to close the message box.</span></span>

5. <span data-ttu-id="584e6-202">V nabídce **ladění** klikněte na položku **Zastavit ladění**.</span><span class="sxs-lookup"><span data-stu-id="584e6-202">On the **Debug** menu, click **Stop debugging**.</span></span>

     <span data-ttu-id="584e6-203">Ladicí relace se zavře.</span><span class="sxs-lookup"><span data-stu-id="584e6-203">The debug session closes.</span></span>

6. <span data-ttu-id="584e6-204">Pokud jste dokončili experimentování, můžete kliknout na **Zavřít projekt** v nabídce **soubor** a po zobrazení výzvy projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="584e6-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>

## <a name="next-steps"></a><span data-ttu-id="584e6-205">Další kroky</span><span class="sxs-lookup"><span data-stu-id="584e6-205">Next Steps</span></span>

<span data-ttu-id="584e6-206">Tento projekt můžete vylepšit tím, že provedete nějaké změny.</span><span class="sxs-lookup"><span data-stu-id="584e6-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="584e6-207">Můžete například zobrazit seznam dostupných uložených procedur v seznamu a nechat uživatele vybrat, které procedury provést.</span><span class="sxs-lookup"><span data-stu-id="584e6-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="584e6-208">Výstup sestav můžete také streamovat do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="584e6-208">You could also stream the output of the reports to a text file.</span></span>

## <a name="see-also"></a><span data-ttu-id="584e6-209">Viz také:</span><span class="sxs-lookup"><span data-stu-id="584e6-209">See also</span></span>

- [<span data-ttu-id="584e6-210">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="584e6-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="584e6-211">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="584e6-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
