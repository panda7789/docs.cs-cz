---
title: 'Návod: Použití jen uložených procedur (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 22db347afb45b981602d5a92516271f75b8e4359
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648683"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="b5539-102">Návod: Použití jen uložených procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5539-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="b5539-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům pomocí uložených procedur komponentami TableAdapter pouze.</span><span class="sxs-lookup"><span data-stu-id="b5539-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="b5539-104">Tento přístup se často používá ve správci databází a omezit způsob přístupu k úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="b5539-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5539-105">Můžete také použít uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacím přepsat výchozí chování, zejména u `Create`, `Update`, a `Delete` procesy.</span><span class="sxs-lookup"><span data-stu-id="b5539-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="b5539-106">Další informace najdete v tématu [přizpůsobení Insert, Update a operace odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b5539-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="b5539-107">Pro účely tohoto názorného postupu budete používat dvě metody, které byly namapovány na uložené procedury v ukázkové databázi Northwind: CustOrdersDetail a CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="b5539-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="b5539-108">Mapování nastane, když spustíte nástroj příkazového řádku SqlMetal generuje soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b5539-108">The mapping occurs when you run the SqlMetal command-line tool to generate a Visual Basic file.</span></span> <span data-ttu-id="b5539-109">Další informace najdete v části požadavky později v tomto názorném postupu.</span><span class="sxs-lookup"><span data-stu-id="b5539-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="b5539-110">Tento názorný postup nevyžaduje [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5539-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="b5539-111">Vývojáři, kteří používají Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] k implementaci funkcionality uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="b5539-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="b5539-112">Zobrazit [LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="b5539-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="b5539-113">Tento návod byl napsán s použitím vývojového nastavení jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b5539-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b5539-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5539-114">Prerequisites</span></span>  
 <span data-ttu-id="b5539-115">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="b5539-115">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="b5539-116">Tento návod používá vyhrazené složky ("c:\linqtest3") pro uložení souborů.</span><span class="sxs-lookup"><span data-stu-id="b5539-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="b5539-117">Vytvoření této složky, před zahájením návodu.</span><span class="sxs-lookup"><span data-stu-id="b5539-117">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="b5539-118">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="b5539-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="b5539-119">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="b5539-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="b5539-120">Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="b5539-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="b5539-121">Po stažení databáze, zkopírujte do složky c:\linqtest3 northwnd.mdf souboru.</span><span class="sxs-lookup"><span data-stu-id="b5539-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
- <span data-ttu-id="b5539-122">Soubor kódu jazyka Visual Basic generují z databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="b5539-122">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="b5539-123">Tento návod byl napsán s použitím nástroje SqlMetal s následujícím příkazovým řádkem:</span><span class="sxs-lookup"><span data-stu-id="b5539-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="b5539-124">**SqlMetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions / pluralize**</span><span class="sxs-lookup"><span data-stu-id="b5539-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="b5539-125">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b5539-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b5539-126">Přehled</span><span class="sxs-lookup"><span data-stu-id="b5539-126">Overview</span></span>  
 <span data-ttu-id="b5539-127">Tento názorný postup se skládá z šesti hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="b5539-127">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="b5539-128">Nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5539-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="b5539-129">Přidání System.Data.Linq sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="b5539-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
- <span data-ttu-id="b5539-130">Přidání kódu databázový soubor do projektu.</span><span class="sxs-lookup"><span data-stu-id="b5539-130">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="b5539-131">Vytvoření připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="b5539-131">Creating a connection to the database.</span></span>  
  
- <span data-ttu-id="b5539-132">Nastavení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b5539-132">Setting up the user interface.</span></span>  
  
- <span data-ttu-id="b5539-133">Spuštění a testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5539-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="b5539-134">Vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="b5539-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="b5539-135">V této první úloze vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="b5539-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="b5539-136">K vytvoření LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="b5539-136">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="b5539-137">V sadě Visual Studio **souboru** nabídky, klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="b5539-137">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="b5539-138">V **typy projektů** v podokně **nový projekt** dialogového okna rozbalte **jazyka Visual Basic**a potom klikněte na tlačítko **Windows**.</span><span class="sxs-lookup"><span data-stu-id="b5539-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3. <span data-ttu-id="b5539-139">V **šablony** podokně klikněte na tlačítko **formulářová aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="b5539-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="b5539-140">V **název** zadejte **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="b5539-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="b5539-141">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5539-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="b5539-142">Otevře se Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="b5539-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="b5539-143">Přidání LINQ na odkaz na sestavení SQL</span><span class="sxs-lookup"><span data-stu-id="b5539-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="b5539-144">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není součástí standardní šablony aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b5539-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="b5539-145">Budete muset přidat sestavení sami, jak je popsáno v následujících krocích:</span><span class="sxs-lookup"><span data-stu-id="b5539-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="b5539-146">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="b5539-146">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="b5539-147">V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="b5539-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2. <span data-ttu-id="b5539-148">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="b5539-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3. <span data-ttu-id="b5539-149">V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5539-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b5539-150">Sestavení se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="b5539-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b5539-151">Přidání souboru Northwind kódu do projektu</span><span class="sxs-lookup"><span data-stu-id="b5539-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="b5539-152">Tento krok předpokládá, že jste použili nástroj SqlMetal ke generování souboru kódu z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="b5539-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="b5539-153">Další informace najdete v oddílu požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="b5539-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b5539-154">Chcete-li přidat soubor kódu northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="b5539-154">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="b5539-155">Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="b5539-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="b5539-156">V **přidat existující položku** dialogové okno, přesunout do c:\linqtest3\northwind.vb a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="b5539-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="b5539-157">Soubor northwind.vb je přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="b5539-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="b5539-158">Vytváří se připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="b5539-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="b5539-159">V tomto kroku definujete připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="b5539-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="b5539-160">Tento návod používá jako cestu "c:\linqtest3\northwnd.mdf".</span><span class="sxs-lookup"><span data-stu-id="b5539-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="b5539-161">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="b5539-161">To create the database connection</span></span>  
  
1. <span data-ttu-id="b5539-162">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1.vb**a potom klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="b5539-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="b5539-163">`Class Form1` Zobrazí se v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="b5539-163">`Class Form1` appears in the code editor.</span></span>  
  
2. <span data-ttu-id="b5539-164">Zadejte následující kód do `Form1` blok kódu:</span><span class="sxs-lookup"><span data-stu-id="b5539-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="b5539-165">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5539-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="b5539-166">V této úloze vytvoříte rozhraní tak, aby uživatelé můžou spouštět uložené procedury pro přístup k datům v databázi.</span><span class="sxs-lookup"><span data-stu-id="b5539-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="b5539-167">V aplikaci, kterou vyvíjíte s tímto názorným postupem můžou uživatelé k datům v databázi pouze pomocí uložených procedur, které jsou vloženy do aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5539-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="b5539-168">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5539-168">To set up the user interface</span></span>  
  
1. <span data-ttu-id="b5539-169">Vraťte se Windows Forms Designer (**Form1.vb[Design]**).</span><span class="sxs-lookup"><span data-stu-id="b5539-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2. <span data-ttu-id="b5539-170">Na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="b5539-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="b5539-171">Otevře se panel nástrojů.</span><span class="sxs-lookup"><span data-stu-id="b5539-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5539-172">Klikněte na tlačítko **automatické skrývání** připínáčku nechat otevřené sady nástrojů, zatímco provádíte zbývající kroky v této části.</span><span class="sxs-lookup"><span data-stu-id="b5539-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="b5539-173">Přetáhněte z panelu nástrojů na dvě tlačítka, dvě textová pole a dva popisky **Form1**.</span><span class="sxs-lookup"><span data-stu-id="b5539-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="b5539-174">Uspořádání ovládacích prvků jako doprovodné ilustrace.</span><span class="sxs-lookup"><span data-stu-id="b5539-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="b5539-175">Rozbalte **Form1** tak, aby snadno umístit ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="b5539-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="b5539-176">Klikněte pravým tlačítkem na **Label1**a potom klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b5539-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="b5539-177">Změnit **Text** vlastnost z **Label1** k **zadejte OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="b5539-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="b5539-178">Stejně jako u **Label2**, změnit **Text** vlastnost z **Label2** k **zadejte ID zákazníka:**.</span><span class="sxs-lookup"><span data-stu-id="b5539-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="b5539-179">Stejným způsobem, změnit **Text** vlastnost **Button1** k **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="b5539-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="b5539-180">Změnit **Text** vlastnost **Button2** k **historie objednávek**.</span><span class="sxs-lookup"><span data-stu-id="b5539-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="b5539-181">Ovládací prvky tlačítka rozšíříte tak, aby veškerý text.</span><span class="sxs-lookup"><span data-stu-id="b5539-181">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="b5539-182">Pro zpracování kliknutí na tlačítko</span><span class="sxs-lookup"><span data-stu-id="b5539-182">To handle button clicks</span></span>  
  
1. <span data-ttu-id="b5539-183">Dvakrát klikněte na panel **OrderDetails** na **Form1** vytvořit `Button1` obslužná rutina události a otevřete editor kódu.</span><span class="sxs-lookup"><span data-stu-id="b5539-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2. <span data-ttu-id="b5539-184">Zadejte následující kód do `Button1` obslužné rutiny:</span><span class="sxs-lookup"><span data-stu-id="b5539-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. <span data-ttu-id="b5539-185">Teď klikněte dvakrát na **Button2** na Form1 vytvořit `Button2` obslužná rutina události a otevřete editor kódu.</span><span class="sxs-lookup"><span data-stu-id="b5539-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4. <span data-ttu-id="b5539-186">Zadejte následující kód do `Button2` obslužné rutiny:</span><span class="sxs-lookup"><span data-stu-id="b5539-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="b5539-187">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="b5539-187">Testing the Application</span></span>  
 <span data-ttu-id="b5539-188">Nyní je čas k testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5539-188">Now it is time to test your application.</span></span> <span data-ttu-id="b5539-189">Všimněte si, že váš kontakt s úložišti dat je omezená na libovolné akce může trvat dvě uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="b5539-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="b5539-190">Tyto akce jsou vrátit produkty zahrnuté pro všechny orderID, které zadáte, nebo vrátit historie produktů seřazených pro jakékoli CustomerID zadáte.</span><span class="sxs-lookup"><span data-stu-id="b5539-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="b5539-191">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="b5539-191">To test the application</span></span>  
  
1. <span data-ttu-id="b5539-192">Stisknutím klávesy F5 spusťte ladění.</span><span class="sxs-lookup"><span data-stu-id="b5539-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="b5539-193">Form1 se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="b5539-193">Form1 appears.</span></span>  
  
2. <span data-ttu-id="b5539-194">V **zadejte OrderID** zadejte **10249** a potom klikněte na tlačítko **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="b5539-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="b5539-195">Okno se zprávou zobrazí seznam produktům zahrnutým v pořadí 10249.</span><span class="sxs-lookup"><span data-stu-id="b5539-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="b5539-196">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="b5539-196">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="b5539-197">V **zadejte CustomerID** zadejte `ALFKI`a potom klikněte na tlačítko **historie objednávek**.</span><span class="sxs-lookup"><span data-stu-id="b5539-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="b5539-198">Okno se zprávou zobrazí seznam historie objednávek pro zákazníka ALFKI.</span><span class="sxs-lookup"><span data-stu-id="b5539-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="b5539-199">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="b5539-199">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="b5539-200">V **zadejte OrderID** zadejte `123`a potom klikněte na tlačítko **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="b5539-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="b5539-201">Zobrazí okno se zprávou "Žádné výsledky."</span><span class="sxs-lookup"><span data-stu-id="b5539-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="b5539-202">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="b5539-202">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="b5539-203">Na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění**.</span><span class="sxs-lookup"><span data-stu-id="b5539-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="b5539-204">Ukončí relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="b5539-204">The debug session closes.</span></span>  
  
6. <span data-ttu-id="b5539-205">Pokud jste dokončili, experimentování, můžete kliknout na **zavřít projekt** na **souboru** nabídky a po zobrazení výzvy uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="b5539-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b5539-206">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b5539-206">Next Steps</span></span>  
 <span data-ttu-id="b5539-207">Tento projekt můžete vylepšit tím, že některé změny.</span><span class="sxs-lookup"><span data-stu-id="b5539-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="b5539-208">Můžete například seznam dostupných uložené procedury v seznamu a mít uživatele, který postup ke spuštění vyberte.</span><span class="sxs-lookup"><span data-stu-id="b5539-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="b5539-209">Může také datový proud výstupu sestavy do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="b5539-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5539-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5539-210">See also</span></span>

- [<span data-ttu-id="b5539-211">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="b5539-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="b5539-212">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="b5539-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
