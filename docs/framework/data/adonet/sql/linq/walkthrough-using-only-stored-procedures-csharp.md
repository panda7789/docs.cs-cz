---
title: 'Návod: Použití jen uložených procedur (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: e5497c1c6bfe032ba272c911217adaa3bd7f4f4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332686"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="a9f5e-102">Návod: Použití jen uložených procedur (C#)</span><span class="sxs-lookup"><span data-stu-id="a9f5e-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>
<span data-ttu-id="a9f5e-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům spuštěním uložené procedury pouze.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="a9f5e-104">Tento přístup se často používá ve správci databází a omezit způsob přístupu k úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9f5e-105">Můžete také použít uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacím přepsat výchozí chování, zejména u `Create`, `Update`, a `Delete` procesy.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="a9f5e-106">Další informace najdete v tématu [přizpůsobení Insert, Update a operace odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a9f5e-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="a9f5e-107">Pro účely tohoto názorného postupu budete používat dvě metody, které byly namapovány na uložené procedury v ukázkové databázi Northwind: CustOrdersDetail a CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="a9f5e-108">Mapování nastane, když spustíte nástroj příkazového řádku SqlMetal k vygenerování C# souboru.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="a9f5e-109">Další informace najdete v části požadavky později v tomto názorném postupu.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="a9f5e-110">Tento názorný postup nevyžaduje [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9f5e-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="a9f5e-111">Vývojáři, kteří používají Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] k implementaci funkcionality uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="a9f5e-112">Zobrazit [LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="a9f5e-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="a9f5e-113">Tento návod byl napsán s použitím Visual C# vývojovým nastavením.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-113">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a9f5e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9f5e-114">Prerequisites</span></span>  
 <span data-ttu-id="a9f5e-115">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="a9f5e-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="a9f5e-116">Tento návod používá vyhrazené složky ("c:\linqtest7") pro uložení souborů.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="a9f5e-117">Vytvoření této složky, před zahájením návodu.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="a9f5e-118">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="a9f5e-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="a9f5e-119">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="a9f5e-120">Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a9f5e-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="a9f5e-121">Po stažení databáze, zkopírujte do složky c:\linqtest7 northwnd.mdf souboru.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>  
  
-   <span data-ttu-id="a9f5e-122">A C# soubor kód generovaný z databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-122">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="a9f5e-123">Tento návod byl napsán s použitím nástroje SqlMetal s následujícím příkazovým řádkem:</span><span class="sxs-lookup"><span data-stu-id="a9f5e-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="a9f5e-124">**SqlMetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / pluralize**</span><span class="sxs-lookup"><span data-stu-id="a9f5e-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="a9f5e-125">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a9f5e-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="a9f5e-126">Přehled</span><span class="sxs-lookup"><span data-stu-id="a9f5e-126">Overview</span></span>  
 <span data-ttu-id="a9f5e-127">Tento názorný postup se skládá z šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="a9f5e-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="a9f5e-128">Nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="a9f5e-129">Přidání System.Data.Linq sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="a9f5e-130">Přidání kódu databázový soubor do projektu.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="a9f5e-131">Vytvoření připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-131">Creating a connection with the database.</span></span>  
  
-   <span data-ttu-id="a9f5e-132">Nastavení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="a9f5e-133">Spuštění a testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="a9f5e-134">Vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="a9f5e-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="a9f5e-135">V této první úloze vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="a9f5e-136">K vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="a9f5e-136">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="a9f5e-137">V sadě Visual Studio **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="a9f5e-138">V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#** .</span><span class="sxs-lookup"><span data-stu-id="a9f5e-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="a9f5e-139">V **šablony** podokně klikněte na tlačítko **formulářová aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="a9f5e-140">V **název** zadejte **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="a9f5e-141">V **umístění** pole, ověřte, kam chcete uložit soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-141">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="a9f5e-142">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="a9f5e-143">Otevře se Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="a9f5e-144">Přidání LINQ na odkaz na sestavení SQL</span><span class="sxs-lookup"><span data-stu-id="a9f5e-144">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="a9f5e-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není součástí standardní šablony aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="a9f5e-146">Budete muset přidat sestavení sami, jak je popsáno v následujících krocích:</span><span class="sxs-lookup"><span data-stu-id="a9f5e-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="a9f5e-147">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="a9f5e-147">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="a9f5e-148">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="a9f5e-149">V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a9f5e-150">Sestavení se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="a9f5e-151">Přidání souboru Northwind kódu do projektu</span><span class="sxs-lookup"><span data-stu-id="a9f5e-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="a9f5e-152">Tento krok předpokládá, že jste použili nástroj SqlMetal ke generování souboru kódu z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="a9f5e-153">Další informace najdete v oddílu požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="a9f5e-154">Chcete-li přidat soubor kódu northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="a9f5e-154">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="a9f5e-155">Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="a9f5e-156">V **přidat existující položku** dialogové okno, přesunout do c:\linqtest7\northwind.cs a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="a9f5e-157">Soubor northwind.cs je přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-157">The northwind.cs file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="a9f5e-158">Vytváří se připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="a9f5e-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="a9f5e-159">V tomto kroku definujete připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="a9f5e-160">Tento návod používá jako cestu "c:\linqtest7\northwnd.mdf".</span><span class="sxs-lookup"><span data-stu-id="a9f5e-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="a9f5e-161">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="a9f5e-161">To create the database connection</span></span>  
  
1. <span data-ttu-id="a9f5e-162">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1.cs**a potom klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="a9f5e-163">Zadejte následující kód do `Form1` třídy:</span><span class="sxs-lookup"><span data-stu-id="a9f5e-163">Type the following code into the `Form1` class:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="a9f5e-164">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9f5e-164">Setting up the User Interface</span></span>  
 <span data-ttu-id="a9f5e-165">V této úloze nastavíte rozhraní tak, aby uživatelé můžou spouštět uložené procedury pro přístup k datům v databázi.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="a9f5e-166">V aplikacích, které vyvíjíte s tímto názorným postupem můžou uživatelé k datům v databázi pouze pomocí uložených procedur, které jsou vloženy do aplikace.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="a9f5e-167">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9f5e-167">To set up the user interface</span></span>  
  
1. <span data-ttu-id="a9f5e-168">Vraťte se Windows Forms Designer (**Form1.cs[Design]**).</span><span class="sxs-lookup"><span data-stu-id="a9f5e-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>  
  
2. <span data-ttu-id="a9f5e-169">Na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-169">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="a9f5e-170">Otevře se panel nástrojů.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-170">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9f5e-171">Klikněte na tlačítko **automatické skrývání** připínáčku nechat otevřené sady nástrojů, zatímco provádíte zbývající kroky v této části.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="a9f5e-172">Přetáhněte z panelu nástrojů na dvě tlačítka, dvě textová pole a dva popisky **Form1**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="a9f5e-173">Uspořádání ovládacích prvků jako doprovodné ilustrace.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="a9f5e-174">Rozbalte **Form1** tak, aby snadno umístit ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-174">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="a9f5e-175">Klikněte pravým tlačítkem na **label1**a potom klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-175">Right-click **label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="a9f5e-176">Změnit **Text** vlastnost z **label1** k **zadejte OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="a9f5e-177">Stejně jako u **label2**, změnit **Text** vlastnost z **label2** k **zadejte ID zákazníka:**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="a9f5e-178">Stejným způsobem, změnit **Text** vlastnost **button1** k **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="a9f5e-179">Změnit **Text** vlastnost **button2** k **historie objednávek**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-179">Change the **Text** property for **button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="a9f5e-180">Ovládací prvky tlačítka rozšíříte tak, aby veškerý text.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-180">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="a9f5e-181">Pro zpracování kliknutí na tlačítko</span><span class="sxs-lookup"><span data-stu-id="a9f5e-181">To handle button clicks</span></span>  
  
1. <span data-ttu-id="a9f5e-182">Dvakrát klikněte na panel **OrderDetails** na **Form1** obslužná rutina události button1 otevřít v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>  
  
2. <span data-ttu-id="a9f5e-183">Zadejte následující kód do `button1` obslužné rutiny:</span><span class="sxs-lookup"><span data-stu-id="a9f5e-183">Type the following code into the `button1` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3. <span data-ttu-id="a9f5e-184">Teď klikněte dvakrát na **button2** na **Form1** otevřít `button2` obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="a9f5e-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>  
  
4. <span data-ttu-id="a9f5e-185">Zadejte následující kód do `button2` obslužné rutiny:</span><span class="sxs-lookup"><span data-stu-id="a9f5e-185">Type the following code into the `button2` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="a9f5e-186">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="a9f5e-186">Testing the Application</span></span>  
 <span data-ttu-id="a9f5e-187">Nyní je čas k testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-187">Now it is time to test your application.</span></span> <span data-ttu-id="a9f5e-188">Všimněte si, že váš kontakt s úložišti dat je omezená na libovolné akce může trvat dvě uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="a9f5e-189">Tyto akce jsou vrátit produkty zahrnuté pro všechny orderID, které zadáte, nebo vrátit historie produktů seřazených pro jakékoli CustomerID zadáte.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="a9f5e-190">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="a9f5e-190">To test the application</span></span>  
  
1. <span data-ttu-id="a9f5e-191">Stisknutím klávesy F5 spusťte ladění.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-191">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="a9f5e-192">Form1 se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-192">Form1 appears.</span></span>  
  
2. <span data-ttu-id="a9f5e-193">V **zadejte OrderID** zadejte `10249`a potom klikněte na tlačítko **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="a9f5e-194">Okno se zprávou zobrazí seznam produktům zahrnutým v pořadí 10249.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-194">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="a9f5e-195">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-195">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="a9f5e-196">V **zadejte CustomerID** zadejte `ALFKI`a potom klikněte na tlačítko **historie objednávek**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="a9f5e-197">Zobrazí se okno se zprávou, která obsahuje seznam historie objednávek pro zákazníka ALFKI.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-197">A message box appears that lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="a9f5e-198">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-198">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="a9f5e-199">V **zadejte OrderID** zadejte `123`a potom klikněte na tlačítko **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="a9f5e-200">Zobrazí se okno se zprávou, která se zobrazí "Žádné výsledky."</span><span class="sxs-lookup"><span data-stu-id="a9f5e-200">A message box appears that displays "No results."</span></span>  
  
     <span data-ttu-id="a9f5e-201">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-201">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="a9f5e-202">Na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění**.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-202">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="a9f5e-203">Ukončí relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-203">The debug session closes.</span></span>  
  
6. <span data-ttu-id="a9f5e-204">Pokud jste dokončili, experimentování, můžete kliknout na **zavřít projekt** na **souboru** nabídky a po zobrazení výzvy uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a9f5e-205">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a9f5e-205">Next Steps</span></span>  
 <span data-ttu-id="a9f5e-206">Tento projekt můžete vylepšit tím, že některé změny.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="a9f5e-207">Můžete například seznam dostupných uložené procedury v seznamu a mít uživatele, který postup ke spuštění vyberte.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="a9f5e-208">Může také datový proud výstupu sestavy do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="a9f5e-208">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f5e-209">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9f5e-209">See also</span></span>

- [<span data-ttu-id="a9f5e-210">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="a9f5e-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="a9f5e-211">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="a9f5e-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
