---
title: "Návod: Použití pouze uložené procedury (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 800cc7d6a1e4aa836ebe75afcbe29a3532ee173a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="ab5c7-102">Návod: Použití pouze uložené procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab5c7-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="ab5c7-103">Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přístup k datům pomocí uložené procedury jenom.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="ab5c7-104">Tento přístup se často používá databázi správci omezit, jak přistupovat k úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab5c7-105">Můžete taky uložené procedury v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace přepsat výchozí chování, zejména pro `Create`, `Update`, a `Delete` procesy.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="ab5c7-106">Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ab5c7-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="ab5c7-107">Pro účely tohoto návodu budete používat dvě metody, které nebyly namapovány na uložené procedury v ukázková databáze Northwind: CustOrdersDetail a CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="ab5c7-108">Mapování nastane, když spustíte nástroj příkazového řádku na SqlMetal ke generování [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] souboru.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-108">The mapping occurs when you run the SqlMetal command-line tool to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] file.</span></span> <span data-ttu-id="ab5c7-109">Další informace najdete v části požadavky dále v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="ab5c7-110">Tento návod na nespoléhá se [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab5c7-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="ab5c7-111">Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít také [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] k implementaci funkcí uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-111">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="ab5c7-112">V tématu [technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="ab5c7-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="ab5c7-113">Tento názorný postup napsané pomocí jazyka Visual Basic – vývojové nastavení.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ab5c7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab5c7-114">Prerequisites</span></span>  
 <span data-ttu-id="ab5c7-115">Tento postup vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="ab5c7-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="ab5c7-116">Tento návod používá k uložení souborů vyhrazené složky ("c:\linqtest3").</span><span class="sxs-lookup"><span data-stu-id="ab5c7-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="ab5c7-117">Než začnete návodu, vytvořte této složky.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="ab5c7-118">Ukázkovou databázi Northwind</span><span class="sxs-lookup"><span data-stu-id="ab5c7-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="ab5c7-119">Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="ab5c7-120">Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="ab5c7-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="ab5c7-121">Po stažení databázi, zkopírujte soubor northwnd.mdf ke složce c:\linqtest3.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
-   <span data-ttu-id="ab5c7-122">A [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] vygenerovaném z databáze Northwind souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-122">A [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="ab5c7-123">Tento názorný postup byla zapsána pomocí nástroje SqlMetal s následující příkazový řádek:</span><span class="sxs-lookup"><span data-stu-id="ab5c7-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="ab5c7-124">**SqlMetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions / pluralizovat**</span><span class="sxs-lookup"><span data-stu-id="ab5c7-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="ab5c7-125">Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ab5c7-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ab5c7-126">Přehled</span><span class="sxs-lookup"><span data-stu-id="ab5c7-126">Overview</span></span>  
 <span data-ttu-id="ab5c7-127">Tento názorný postup se skládá z šesti hlavní úlohy:</span><span class="sxs-lookup"><span data-stu-id="ab5c7-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="ab5c7-128">Nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab5c7-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="ab5c7-129">Přidání System.Data.Linq sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="ab5c7-130">Přidání souboru kódu databáze do projektu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="ab5c7-131">Vytvoření připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-131">Creating a connection to the database.</span></span>  
  
-   <span data-ttu-id="ab5c7-132">Nastavení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="ab5c7-133">Spuštění a testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="ab5c7-134">Vytváření dotazu LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="ab5c7-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="ab5c7-135">V této úloze první vytvoříte [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] řešení, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-135">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="ab5c7-136">Chcete-li vytvořit LINQ to SQL řešení</span><span class="sxs-lookup"><span data-stu-id="ab5c7-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="ab5c7-137">Na [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **soubor** nabídky, klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-137">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="ab5c7-138">V **typy projektů** v podokně **nový projekt** dialogové okno, rozbalte seznam **jazyka Visual Basic**a potom klikněte na **Windows**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="ab5c7-139">V **šablony** podokně klikněte na tlačítko **formulářové aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="ab5c7-140">V **název** zadejte **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="ab5c7-141">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="ab5c7-142">Otevře se Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="ab5c7-143">Přidávání do odkaz sestavení SQL LINQ</span><span class="sxs-lookup"><span data-stu-id="ab5c7-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="ab5c7-144">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sestavení není součástí standardní šablona formulářové aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="ab5c7-145">Budete muset přidat sestavení sami, jak je popsáno v následujících krocích:</span><span class="sxs-lookup"><span data-stu-id="ab5c7-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="ab5c7-146">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="ab5c7-146">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="ab5c7-147">V **Průzkumníku řešení**, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2.  <span data-ttu-id="ab5c7-148">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="ab5c7-149">V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ab5c7-150">Je sestavení přidáno do projektu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="ab5c7-151">Přidání souboru Northwind kódu do projektu</span><span class="sxs-lookup"><span data-stu-id="ab5c7-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="ab5c7-152">Tento krok předpokládá, že jste použili nástroj SqlMetal generování souboru kódu na základě ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="ab5c7-153">Další informace najdete v části požadavky dříve v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="ab5c7-154">Přidání souboru northwind kódu do projektu</span><span class="sxs-lookup"><span data-stu-id="ab5c7-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="ab5c7-155">Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="ab5c7-156">V **přidat existující položku** přesunout do c:\linqtest3\northwind.vb dialogové okno a pak klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="ab5c7-157">Soubor northwind.vb je přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="ab5c7-158">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="ab5c7-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="ab5c7-159">V tomto kroku definujete ukázková databáze Northwind připojení.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="ab5c7-160">Tento návod používá jako cestu "c:\linqtest3\northwnd.mdf".</span><span class="sxs-lookup"><span data-stu-id="ab5c7-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="ab5c7-161">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="ab5c7-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="ab5c7-162">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Form1.vb**a potom klikněte na **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="ab5c7-163">`Class Form1`Zobrazí se v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-163">`Class Form1` appears in the code editor.</span></span>  
  
2.  <span data-ttu-id="ab5c7-164">Zadejte následující kód do `Form1` blok kódu:</span><span class="sxs-lookup"><span data-stu-id="ab5c7-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="ab5c7-165">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab5c7-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="ab5c7-166">V této úloze vytvořit rozhraní tak, aby uživatelé mohou spouštět uložené procedury pro přístup k datům v databázi.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="ab5c7-167">V aplikaci, která vyvíjíte v tomto průvodci uživatelé můžou používat data v databázi jen pomocí uložené procedury vloženy do aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="ab5c7-168">Nastavení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab5c7-168">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="ab5c7-169">Návrhář formulářů vraťte se do systému Windows (**Form1.vb[Design]**).</span><span class="sxs-lookup"><span data-stu-id="ab5c7-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2.  <span data-ttu-id="ab5c7-170">Na **zobrazení** nabídky, klikněte na tlačítko **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="ab5c7-171">Otevřete panel nástrojů.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab5c7-172">Klikněte **autohide –** připínáček nechat otevřené sady nástrojů při provádění zbývající kroky v této části.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="ab5c7-173">Přetáhněte dvě tlačítka, dvou textových polí a dva popisky z panelu nástrojů na **Form1**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="ab5c7-174">Uspořádání ovládacích prvků jako doprovodné obrázku.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="ab5c7-175">Rozbalte položku **Form1** tak, aby snadno umístit ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="ab5c7-176">Klikněte pravým tlačítkem na **Label1**a potom klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="ab5c7-177">Změna **Text** vlastnost z **Label1** k **zadejte OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="ab5c7-178">Stejným způsobem pro **Label2**, změnit **Text** vlastnost z **Label2** k **zadejte CustomerID:**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="ab5c7-179">Stejným způsobem, změnit **Text** vlastnost pro **Button1** k **pořadí podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="ab5c7-180">Změna **Text** vlastnost pro **Button2** k **historie objednávek**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="ab5c7-181">Ovládací prvky tlačítek rozšíříte tak, aby veškerý text.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-181">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="ab5c7-182">Pro zpracování kliknutí na tlačítko</span><span class="sxs-lookup"><span data-stu-id="ab5c7-182">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="ab5c7-183">Klikněte dvakrát na **pořadí podrobnosti** na **Form1** vytvořit `Button1` obslužné rutiny události a otevřete editor kódu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2.  <span data-ttu-id="ab5c7-184">Zadejte následující kód do `Button1` obslužné rutiny:</span><span class="sxs-lookup"><span data-stu-id="ab5c7-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  <span data-ttu-id="ab5c7-185">Nyní klikněte dvakrát na **Button2** na Form1 vytvořit `Button2` obslužné rutiny události a otevřete editor kódu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4.  <span data-ttu-id="ab5c7-186">Zadejte následující kód do `Button2` obslužné rutiny:</span><span class="sxs-lookup"><span data-stu-id="ab5c7-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="ab5c7-187">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="ab5c7-187">Testing the Application</span></span>  
 <span data-ttu-id="ab5c7-188">Nyní je čas k testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-188">Now it is time to test your application.</span></span> <span data-ttu-id="ab5c7-189">Všimněte si, že vaše kontaktu s úložišti dat je omezená na libovolné akce může trvat dvě uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="ab5c7-190">Tyto akce jsou vrátit produkty, které jsou zahrnuté pro všechny orderID, které zadáte, nebo pro návrat historii produktů seřazených pro všechny CustomerID zadáte.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="ab5c7-191">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="ab5c7-191">To test the application</span></span>  
  
1.  <span data-ttu-id="ab5c7-192">Stisknutím klávesy F5 spusťte ladění.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="ab5c7-193">Zobrazí se Form1.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-193">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="ab5c7-194">V **zadejte OrderID** zadejte **10249** a pak klikněte na **pořadí podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="ab5c7-195">Okno se zprávou seznamy produktů, zahrnuté v pořadí 10249.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="ab5c7-196">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-196">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="ab5c7-197">V **zadejte CustomerID** zadejte `ALFKI`a potom klikněte na **historie objednávek**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="ab5c7-198">Okno se zprávou uvádí historie objednávek pro zákazníka ALFKI.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="ab5c7-199">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-199">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="ab5c7-200">V **zadejte OrderID** zadejte `123`a potom klikněte na **pořadí podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="ab5c7-201">Zobrazí okno se zprávou "Žádné výsledky."</span><span class="sxs-lookup"><span data-stu-id="ab5c7-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="ab5c7-202">Klikněte na tlačítko **OK** zavřete okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-202">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="ab5c7-203">Na **ladění** nabídky, klikněte na tlačítko **Zastavte ladění**.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="ab5c7-204">Zavře relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-204">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="ab5c7-205">Pokud dokončíte experimentování, můžete kliknout na **zavřít projekt** na **souboru** nabídce a po zobrazení výzvy uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ab5c7-206">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ab5c7-206">Next Steps</span></span>  
 <span data-ttu-id="ab5c7-207">Tento projekt můžete zvýšit tak, že některé změny.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="ab5c7-208">Můžete například seznam dostupných uložené procedury v seznamu a mít uživatele, vyberte který postup provést.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="ab5c7-209">Výstup sestavy do textového souboru může také datového proudu.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5c7-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab5c7-210">See Also</span></span>  
 [<span data-ttu-id="ab5c7-211">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="ab5c7-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="ab5c7-212">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="ab5c7-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
