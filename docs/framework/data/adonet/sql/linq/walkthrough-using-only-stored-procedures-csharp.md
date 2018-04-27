---
title: 'Návod: Použití pouze uložené procedury (C#)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 4c13e4c12abf17f995bb819ddd7d6337407e3b28
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="9eafa-102">Návod: Použití pouze uložené procedury (C#)</span><span class="sxs-lookup"><span data-stu-id="9eafa-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>
<span data-ttu-id="9eafa-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům spuštěním uložené procedury jenom.</span><span class="sxs-lookup"><span data-stu-id="9eafa-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="9eafa-104">Tento přístup se často používá databázi správci omezit, jak přistupovat k úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="9eafa-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9eafa-105">Můžete taky uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace přepsat výchozí chování, zejména pro `Create`, `Update`, a `Delete` procesy.</span><span class="sxs-lookup"><span data-stu-id="9eafa-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="9eafa-106">Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9eafa-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="9eafa-107">Pro účely tohoto návodu budete používat dvě metody, které nebyly namapovány na uložené procedury v ukázková databáze Northwind: CustOrdersDetail a CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="9eafa-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="9eafa-108">Mapování nastane, když spustíte nástroj příkazového řádku na SqlMetal ke generování souboru C#.</span><span class="sxs-lookup"><span data-stu-id="9eafa-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="9eafa-109">Další informace najdete v části požadavky dále v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="9eafa-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="9eafa-110">Tento návod na nespoléhá se [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9eafa-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="9eafa-111">Vývojáři pomocí sady Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] k implementaci funkcí uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="9eafa-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="9eafa-112">V tématu [technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="9eafa-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="9eafa-113">Tento názorný postup napsané pomocí Visual C# – vývojové nastavení.</span><span class="sxs-lookup"><span data-stu-id="9eafa-113">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9eafa-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9eafa-114">Prerequisites</span></span>  
 <span data-ttu-id="9eafa-115">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="9eafa-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="9eafa-116">Tento návod používá k uložení souborů vyhrazené složky ("c:\linqtest7").</span><span class="sxs-lookup"><span data-stu-id="9eafa-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="9eafa-117">Než začnete návodu, vytvořte této složky.</span><span class="sxs-lookup"><span data-stu-id="9eafa-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="9eafa-118">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="9eafa-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="9eafa-119">Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="9eafa-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="9eafa-120">Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="9eafa-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="9eafa-121">Po stažení databázi, zkopírujte soubor northwnd.mdf ke složce c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="9eafa-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>  
  
-   <span data-ttu-id="9eafa-122">C# soubor kódu vygenerovaném z databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="9eafa-122">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="9eafa-123">Tento názorný postup byla zapsána pomocí nástroje SqlMetal s následující příkazový řádek:</span><span class="sxs-lookup"><span data-stu-id="9eafa-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="9eafa-124">**SqlMetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / pluralizovat**</span><span class="sxs-lookup"><span data-stu-id="9eafa-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="9eafa-125">Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="9eafa-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="9eafa-126">Přehled</span><span class="sxs-lookup"><span data-stu-id="9eafa-126">Overview</span></span>  
 <span data-ttu-id="9eafa-127">Tento názorný postup se skládá z šesti hlavní úlohy:</span><span class="sxs-lookup"><span data-stu-id="9eafa-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="9eafa-128">Nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9eafa-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="9eafa-129">Přidání System.Data.Linq sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="9eafa-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="9eafa-130">Přidání souboru kódu databáze do projektu.</span><span class="sxs-lookup"><span data-stu-id="9eafa-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="9eafa-131">Vytvoření připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="9eafa-131">Creating a connection with the database.</span></span>  
  
-   <span data-ttu-id="9eafa-132">Nastavení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9eafa-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="9eafa-133">Spuštění a testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="9eafa-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="9eafa-134">Vytváření dotazu LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="9eafa-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="9eafa-135">V této úloze první vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="9eafa-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="9eafa-136">Chcete-li vytvořit LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="9eafa-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="9eafa-137">V sadě Visual Studio **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="9eafa-138">V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="9eafa-139">V **šablony** podokně klikněte na tlačítko **formulářové aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="9eafa-140">V **název** zadejte **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="9eafa-141">V **umístění** ověřte, kam chcete uložit soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="9eafa-141">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="9eafa-142">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="9eafa-143">Otevře se Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="9eafa-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="9eafa-144">Přidávání do odkaz sestavení SQL LINQ</span><span class="sxs-lookup"><span data-stu-id="9eafa-144">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="9eafa-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není součástí standardní šablona formulářové aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="9eafa-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="9eafa-146">Budete muset přidat sestavení sami, jak je popsáno v následujících krocích:</span><span class="sxs-lookup"><span data-stu-id="9eafa-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="9eafa-147">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="9eafa-147">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="9eafa-148">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="9eafa-149">V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="9eafa-150">Je sestavení přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="9eafa-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="9eafa-151">Přidání souboru Northwind kódu do projektu</span><span class="sxs-lookup"><span data-stu-id="9eafa-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="9eafa-152">Tento krok předpokládá, že jste použili nástroj SqlMetal generování souboru kódu na základě ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="9eafa-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="9eafa-153">Další informace najdete v části požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="9eafa-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="9eafa-154">Přidání souboru northwind kódu do projektu</span><span class="sxs-lookup"><span data-stu-id="9eafa-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="9eafa-155">Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="9eafa-156">V **přidat existující položku** přesunout do c:\linqtest7\northwind.cs dialogové okno a pak klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="9eafa-157">Soubor northwind.cs je přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="9eafa-157">The northwind.cs file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="9eafa-158">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="9eafa-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="9eafa-159">V tomto kroku definujete ukázková databáze Northwind připojení.</span><span class="sxs-lookup"><span data-stu-id="9eafa-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="9eafa-160">Tento návod používá jako cestu "c:\linqtest7\northwnd.mdf".</span><span class="sxs-lookup"><span data-stu-id="9eafa-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="9eafa-161">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="9eafa-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="9eafa-162">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Form1.cs**a potom klikněte na **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="9eafa-163">Zadejte následující kód do `Form1` třídy:</span><span class="sxs-lookup"><span data-stu-id="9eafa-163">Type the following code into the `Form1` class:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="9eafa-164">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9eafa-164">Setting up the User Interface</span></span>  
 <span data-ttu-id="9eafa-165">V této úloze nastavíte rozhraní tak, aby uživatelé mohou spouštět uložené procedury pro přístup k datům v databázi.</span><span class="sxs-lookup"><span data-stu-id="9eafa-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="9eafa-166">V aplikacích, které vyvíjíte v tomto průvodci uživatelé můžou používat data v databázi jen pomocí uložené procedury vloženy do aplikace.</span><span class="sxs-lookup"><span data-stu-id="9eafa-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="9eafa-167">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9eafa-167">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="9eafa-168">Návrhář formulářů vraťte se do systému Windows (**Form1.cs[Design]**).</span><span class="sxs-lookup"><span data-stu-id="9eafa-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>  
  
2.  <span data-ttu-id="9eafa-169">Na **zobrazení** nabídky, klikněte na tlačítko **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-169">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="9eafa-170">Otevřete panel nástrojů.</span><span class="sxs-lookup"><span data-stu-id="9eafa-170">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9eafa-171">Klikněte **autohide –** připínáček nechat otevřené sady nástrojů při provádění zbývající kroky v této části.</span><span class="sxs-lookup"><span data-stu-id="9eafa-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="9eafa-172">Přetáhněte dvě tlačítka, dvou textových polí a dva popisky z panelu nástrojů na **Form1**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="9eafa-173">Uspořádání ovládacích prvků jako doprovodné obrázku.</span><span class="sxs-lookup"><span data-stu-id="9eafa-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="9eafa-174">Rozbalte položku **Form1** tak, aby snadno umístit ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="9eafa-174">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="9eafa-175">Klikněte pravým tlačítkem na **label1**a potom klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-175">Right-click **label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="9eafa-176">Změna **Text** vlastnost z **label1** k **zadejte OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="9eafa-177">Stejným způsobem pro **label2**, změnit **Text** vlastnost z **label2** k **zadejte CustomerID:**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="9eafa-178">Stejným způsobem, změnit **Text** vlastnost pro **button1** k **pořadí podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="9eafa-179">Změna **Text** vlastnost pro **button2** k **historie objednávek**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-179">Change the **Text** property for **button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="9eafa-180">Ovládací prvky tlačítek rozšíříte tak, aby veškerý text.</span><span class="sxs-lookup"><span data-stu-id="9eafa-180">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="9eafa-181">Pro zpracování kliknutí na tlačítko</span><span class="sxs-lookup"><span data-stu-id="9eafa-181">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="9eafa-182">Klikněte dvakrát na **pořadí podrobnosti** na **Form1** obslužné rutiny události button1 otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="9eafa-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>  
  
2.  <span data-ttu-id="9eafa-183">Zadejte následující kód do `button1` obslužné rutiny:</span><span class="sxs-lookup"><span data-stu-id="9eafa-183">Type the following code into the `button1` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  <span data-ttu-id="9eafa-184">Nyní klikněte dvakrát na **button2** na **Form1** otevřete `button2` obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="9eafa-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>  
  
4.  <span data-ttu-id="9eafa-185">Zadejte následující kód do `button2` obslužné rutiny:</span><span class="sxs-lookup"><span data-stu-id="9eafa-185">Type the following code into the `button2` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="9eafa-186">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="9eafa-186">Testing the Application</span></span>  
 <span data-ttu-id="9eafa-187">Nyní je čas k testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="9eafa-187">Now it is time to test your application.</span></span> <span data-ttu-id="9eafa-188">Všimněte si, že vaše kontaktu s úložišti dat je omezená na libovolné akce může trvat dvě uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="9eafa-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="9eafa-189">Tyto akce jsou vrátit produkty, které jsou zahrnuté pro všechny orderID, které zadáte, nebo pro návrat historii produktů seřazených pro všechny CustomerID zadáte.</span><span class="sxs-lookup"><span data-stu-id="9eafa-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="9eafa-190">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="9eafa-190">To test the application</span></span>  
  
1.  <span data-ttu-id="9eafa-191">Stisknutím klávesy F5 spusťte ladění.</span><span class="sxs-lookup"><span data-stu-id="9eafa-191">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="9eafa-192">Zobrazí se Form1.</span><span class="sxs-lookup"><span data-stu-id="9eafa-192">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="9eafa-193">V **zadejte OrderID** zadejte `10249`a potom klikněte na **pořadí podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="9eafa-194">Okno se zprávou seznamy produktů, zahrnuté v pořadí 10249.</span><span class="sxs-lookup"><span data-stu-id="9eafa-194">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="9eafa-195">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="9eafa-195">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="9eafa-196">V **zadejte CustomerID** zadejte `ALFKI`a potom klikněte na **historie objednávek**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="9eafa-197">Zobrazí se okno se zprávou, která uvádí historie objednávek pro zákazníka ALFKI.</span><span class="sxs-lookup"><span data-stu-id="9eafa-197">A message box appears that lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="9eafa-198">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="9eafa-198">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="9eafa-199">V **zadejte OrderID** zadejte `123`a potom klikněte na **pořadí podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="9eafa-200">Zobrazí se okno se zprávou, která zobrazuje "Žádné výsledky."</span><span class="sxs-lookup"><span data-stu-id="9eafa-200">A message box appears that displays "No results."</span></span>  
  
     <span data-ttu-id="9eafa-201">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="9eafa-201">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="9eafa-202">Na **ladění** nabídky, klikněte na tlačítko **Zastavte ladění**.</span><span class="sxs-lookup"><span data-stu-id="9eafa-202">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="9eafa-203">Zavře relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="9eafa-203">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="9eafa-204">Pokud dokončíte experimentování, můžete kliknout na **zavřít projekt** na **souboru** nabídce a po zobrazení výzvy uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="9eafa-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9eafa-205">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9eafa-205">Next Steps</span></span>  
 <span data-ttu-id="9eafa-206">Tento projekt můžete zvýšit tak, že některé změny.</span><span class="sxs-lookup"><span data-stu-id="9eafa-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="9eafa-207">Můžete například seznam dostupných uložené procedury v seznamu a mít uživatele, vyberte který postup provést.</span><span class="sxs-lookup"><span data-stu-id="9eafa-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="9eafa-208">Výstup sestavy do textového souboru může také datového proudu.</span><span class="sxs-lookup"><span data-stu-id="9eafa-208">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eafa-209">Viz také</span><span class="sxs-lookup"><span data-stu-id="9eafa-209">See Also</span></span>  
 [<span data-ttu-id="9eafa-210">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="9eafa-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="9eafa-211">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="9eafa-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
