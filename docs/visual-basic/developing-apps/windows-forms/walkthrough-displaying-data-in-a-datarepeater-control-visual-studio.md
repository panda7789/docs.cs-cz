---
title: "Návod: Zobrazení dat v ovládacím prvku DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6f0cf690b816d57dc4a2646eb82d649727d033a9
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="91e29-102">Návod: Zobrazení dat v ovládacím prvku DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="91e29-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="91e29-103">Tento názorný postup obsahuje základní scénář zahájení dokončení pro zobrazení vázaných dat v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="91e29-104">Předpoklad</span><span class="sxs-lookup"><span data-stu-id="91e29-104">Prerequisite</span></span>  
 <span data-ttu-id="91e29-105">Tento postup vyžaduje ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="91e29-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="91e29-106">Pokud jste tuto databázi ve svém vývojovém počítači, si můžete stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).</span><span class="sxs-lookup"><span data-stu-id="91e29-106">If you do not have this database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).</span></span> <span data-ttu-id="91e29-107">Pokyny najdete v tématu [stažení ukázkové databáze](../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="91e29-107">For instructions, see [Downloading Sample Databases](../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="91e29-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="91e29-108">Overview</span></span>  
 <span data-ttu-id="91e29-109">První část tohoto návodu se skládá z čtyři hlavní úkoly:</span><span class="sxs-lookup"><span data-stu-id="91e29-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="91e29-110">Vytvoření řešení.</span><span class="sxs-lookup"><span data-stu-id="91e29-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="91e29-111">Přidání <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="91e29-112">Přidání zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="91e29-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="91e29-113">Přidání ovládacích prvků vázaných na data.</span><span class="sxs-lookup"><span data-stu-id="91e29-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="91e29-114">Vytváření řešení DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="91e29-115">V prvním kroku vytvořte projekt a řešení.</span><span class="sxs-lookup"><span data-stu-id="91e29-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="91e29-116">Chcete-li vytvořit řešení DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="91e29-117">V sadě Visual Studio **soubor** nabídky, klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="91e29-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="91e29-118">V **typy projektů** v podokně **nový projekt** dialogové okno, rozbalte seznam **jazyka Visual Basic**a potom klikněte na **Windows**.</span><span class="sxs-lookup"><span data-stu-id="91e29-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="91e29-119">V **šablony** podokně klikněte na tlačítko **formulářové aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="91e29-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="91e29-120">V **název** zadejte `DataRepeaterApp`.</span><span class="sxs-lookup"><span data-stu-id="91e29-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="91e29-121">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="91e29-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="91e29-122">Otevře se Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="91e29-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="91e29-123">Vyberte formuláře v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="91e29-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="91e29-124">V **vlastnosti** nastavte **velikost** vlastnost `800, 700`.</span><span class="sxs-lookup"><span data-stu-id="91e29-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="91e29-125">Přidání ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="91e29-126">V tomto kroku přidáte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku do formuláře.</span><span class="sxs-lookup"><span data-stu-id="91e29-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="91e29-127">Přidání ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="91e29-128">Na **zobrazení** nabídky, klikněte na tlačítko **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="91e29-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="91e29-129">**Sada nástrojů** otevře.</span><span class="sxs-lookup"><span data-stu-id="91e29-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="91e29-130">Vyberte **PowerPacks jazyka Visual Basic** kartě.</span><span class="sxs-lookup"><span data-stu-id="91e29-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="91e29-131">Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> na ovládací prvek **Form1**.</span><span class="sxs-lookup"><span data-stu-id="91e29-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="91e29-132">V okně vlastnosti nastavit **umístění** vlastnost `0, 25`.</span><span class="sxs-lookup"><span data-stu-id="91e29-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="91e29-133">Nastavte **velikost** vlastnost `460, 600`.</span><span class="sxs-lookup"><span data-stu-id="91e29-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="91e29-134">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="91e29-134">Adding a Data Source</span></span>  
 <span data-ttu-id="91e29-135">V tomto kroku přidáte zdroj dat pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="91e29-136">Chcete-li přidat zdroje dat</span><span class="sxs-lookup"><span data-stu-id="91e29-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="91e29-137">Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.</span><span class="sxs-lookup"><span data-stu-id="91e29-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="91e29-138">V **zdroje dat** okně klikněte na tlačítko **přidat nový zdroj dat**.</span><span class="sxs-lookup"><span data-stu-id="91e29-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="91e29-139">Vyberte **databáze** na **zvolte typ zdroje dat** a pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="91e29-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="91e29-140">Na **vybrat datové připojení** proveďte některý z následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="91e29-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="91e29-141">Pokud je k dispozici v rozevíracím seznamu připojení dat k ukázková databáze Northwind, klikněte na něj.</span><span class="sxs-lookup"><span data-stu-id="91e29-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="91e29-142">-nebo-</span><span class="sxs-lookup"><span data-stu-id="91e29-142">-or-</span></span>  
  
    -   <span data-ttu-id="91e29-143">Klikněte na tlačítko **nové připojení** konfigurace nové datové připojení.</span><span class="sxs-lookup"><span data-stu-id="91e29-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="91e29-144">Další informace najdete v tématu [postupy: vytvoření připojení databáze serveru SQL Server](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d).</span><span class="sxs-lookup"><span data-stu-id="91e29-144">For more information, see [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d).</span></span>  
  
5.  <span data-ttu-id="91e29-145">Pokud databáze vyžaduje heslo, vyberte možnost obsahují citlivá data, a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="91e29-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91e29-146">Pokud se zobrazí dialogové okno, klikněte na tlačítko **Ano** k uložení souboru do projektu.</span><span class="sxs-lookup"><span data-stu-id="91e29-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="91e29-147">Klikněte na tlačítko **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.</span><span class="sxs-lookup"><span data-stu-id="91e29-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="91e29-148">Rozbalte **tabulky** uzlu **zvolte si databázové objekty** stránky.</span><span class="sxs-lookup"><span data-stu-id="91e29-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="91e29-149">Zaškrtněte políčka vedle **zákazníci** a **objednávky** tabulky a pak klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="91e29-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="91e29-150">**NorthwindDataSet** se přidá do projektu a **zákazníci** a **objednávky** tabulky se zobrazí v **zdroje dat** okno.</span><span class="sxs-lookup"><span data-stu-id="91e29-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="91e29-151">Přidání ovládacích prvků vázaných na Data</span><span class="sxs-lookup"><span data-stu-id="91e29-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="91e29-152">V tomto kroku přidáte ovládací prvky vázané na data na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="91e29-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="91e29-153">Přidání ovládacích prvků vázaných na data</span><span class="sxs-lookup"><span data-stu-id="91e29-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="91e29-154">V **zdroje dat** okně vyberte nejvyšší uzel **zákazníci** tabulky.</span><span class="sxs-lookup"><span data-stu-id="91e29-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="91e29-155">Změňte typ tabulky na **podrobnosti** kliknutím **podrobnosti** v rozevíracím seznamu na uzlu tabulky.</span><span class="sxs-lookup"><span data-stu-id="91e29-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="91e29-156">Vyberte **zákazníci** tabulky uzel a přetáhněte ji na oblast šablony položky (horní oblasti) z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="91e29-157">A <xref:System.Windows.Forms.BindingNavigator> ovládací prvek přidán do formuláře a **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, a **CustomersBindingNavigator** součásti jsou přidány do komponent.</span><span class="sxs-lookup"><span data-stu-id="91e29-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="91e29-158">Vyberte všechny pole a jejich přidružené popisky a umístit je téměř je levý okraj oblast šablony položky.</span><span class="sxs-lookup"><span data-stu-id="91e29-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="91e29-159">Vyberte pole, posledních pět (**oblast**, **PSČ**, **země**, **Phone**, a **Fax**) a jejich přidružené popisky a přesuňte je v provozu a napravo od pole prvních šesti.</span><span class="sxs-lookup"><span data-stu-id="91e29-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="91e29-160">Vyberte šablony položky (horní oblast ovládacího prvku).</span><span class="sxs-lookup"><span data-stu-id="91e29-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="91e29-161">V okně vlastnosti nastavit **velikost** vlastnost `427, 170`.</span><span class="sxs-lookup"><span data-stu-id="91e29-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="91e29-162">V tuto chvíli máte funkční aplikaci, která se zobrazí seznam opakovaných zákazníků.</span><span class="sxs-lookup"><span data-stu-id="91e29-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="91e29-163">Můžete stisknutím klávesy F5 aplikaci spustit, změnit data a přidat nebo odstranit záznamy o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="91e29-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="91e29-164">V dalším volitelným krokům, se dozvíte, jak přizpůsobit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="91e29-165">Další kroky (volitelné)</span><span class="sxs-lookup"><span data-stu-id="91e29-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="91e29-166">Tato část průvodce se skládá ze čtyř volitelné úkoly:</span><span class="sxs-lookup"><span data-stu-id="91e29-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="91e29-167">Změna vzhledu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="91e29-168">Zabránění uživatelům v přidávání nebo odstraňování záznamů.</span><span class="sxs-lookup"><span data-stu-id="91e29-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="91e29-169">Přidání schopností vyhledávání do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="91e29-170">Přidávání seznamu a podrobností tabulka, která se <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="91e29-171">Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="91e29-172">V tomto kroku volitelné změníte `BackColor` z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="91e29-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="91e29-173">Je také přidat kód pro zobrazení řádek v střídavých barvy a při změně štítku na `ForeColor` podmíněně.</span><span class="sxs-lookup"><span data-stu-id="91e29-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="91e29-174">Změna vzhledu ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="91e29-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="91e29-175">V Návrháři formulářů vyberte oblast hlavní (dolního) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="91e29-176">V okně vlastnosti nastavit `BackColor` vlastnosti prázdné.</span><span class="sxs-lookup"><span data-stu-id="91e29-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="91e29-177">Dvakrát klikněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> otevření editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="91e29-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="91e29-178">V editoru kódu, události rozevíracího seznamu, klikněte na tlačítko **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="91e29-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="91e29-179">V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužné rutiny události, přidejte následující kód do alternativní `BackColor`:</span><span class="sxs-lookup"><span data-stu-id="91e29-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  <span data-ttu-id="91e29-180">V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužné rutiny události, přidejte následující kód, chcete-li změnit `ForeColor` popisku v závislosti na podmínce:</span><span class="sxs-lookup"><span data-stu-id="91e29-180">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  <span data-ttu-id="91e29-181">Stisknutím klávesy F5 spusťte aplikaci a zobrazit individuální nastavení.</span><span class="sxs-lookup"><span data-stu-id="91e29-181">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="91e29-182">Zabránění uživatelům v přidávání nebo odstraňování záznamů</span><span class="sxs-lookup"><span data-stu-id="91e29-182">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="91e29-183">V tomto kroku volitelné přidáte kód, který zabrání uživatelům v přidávání nebo odstraňování záznamů <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-183">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="91e29-184">Chcete-li zabránit uživatelům v přidávání a odstraňování záznamů</span><span class="sxs-lookup"><span data-stu-id="91e29-184">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="91e29-185">V Návrháři formulářů poklepejte na formulář pro otevření editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="91e29-185">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="91e29-186">Přidejte následující kód, který `Form_Load` událostí:</span><span class="sxs-lookup"><span data-stu-id="91e29-186">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  <span data-ttu-id="91e29-187">V rozevíracím seznamu název třídy, klikněte na **BindingNavigatorDeleteItem**.</span><span class="sxs-lookup"><span data-stu-id="91e29-187">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="91e29-188">V rozevíracím seznamu název metody, klikněte na **EnabledChanged**.</span><span class="sxs-lookup"><span data-stu-id="91e29-188">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="91e29-189">Přidejte následující kód, který `BindingNavigatorDeleteItem_EnabledChanged` obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="91e29-189">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="91e29-190">Tento krok je nezbytný, protože <xref:System.Windows.Forms.BindingSource> povolí **DeleteItem** tlačítko pokaždé, když se změní na aktuální záznam.</span><span class="sxs-lookup"><span data-stu-id="91e29-190">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="91e29-191">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="91e29-191">Press F5 to run the application.</span></span> <span data-ttu-id="91e29-192">Všimněte si, že **DeleteItem** tlačítko k dispozici a nelze odstranit položky po stisknutí klávesy odstranit.</span><span class="sxs-lookup"><span data-stu-id="91e29-192">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="91e29-193">Přidání schopností vyhledávání do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-193">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="91e29-194">V tomto volitelné kroku implementujete schopnost vyhledejte hodnotu v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-194">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="91e29-195">Pokud se řetězec najde, ovládacího prvku vybere položku, která obsahuje hodnotu a posune položky do zobrazení.</span><span class="sxs-lookup"><span data-stu-id="91e29-195">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="91e29-196">Přidání schopností vyhledávání</span><span class="sxs-lookup"><span data-stu-id="91e29-196">To add search capability</span></span>  
  
1.  <span data-ttu-id="91e29-197">Přetažení <xref:System.Windows.Forms.TextBox> řídit z **sada nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-197">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="91e29-198">Umístěte ho <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-198">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="91e29-199">V okně vlastností změňte **název** vlastnost **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="91e29-199">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="91e29-200">Přetažení <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-200">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="91e29-201">Umístěte ho <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-201">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="91e29-202">V okně vlastností změňte **název** vlastnost **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="91e29-202">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="91e29-203">Změna **Text** vlastnost **vyhledávání**.</span><span class="sxs-lookup"><span data-stu-id="91e29-203">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="91e29-204">Dvakrát klikněte <xref:System.Windows.Forms.Button> řídit k otevření editoru kódu a přidejte následující kód do `SearchButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="91e29-204">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  <span data-ttu-id="91e29-205">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="91e29-205">Press F5 to run the application.</span></span> <span data-ttu-id="91e29-206">Zadejte ID zákazníka v **SearchTextBox** a klikněte na **vyhledávání** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="91e29-206">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="91e29-207">Přidávání do DataRepeater hlavní a tabulka podrobností</span><span class="sxs-lookup"><span data-stu-id="91e29-207">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="91e29-208">V tomto kroku volitelné přidejte druhý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení k zobrazení související objednávky pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="91e29-208">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="91e29-209">Chcete-li přidat tabulku seznamu a podrobností</span><span class="sxs-lookup"><span data-stu-id="91e29-209">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="91e29-210">Přetáhněte druhý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="91e29-210">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="91e29-211">V okně vlastnosti nastavit **umístění** vlastnost `465, 25`.</span><span class="sxs-lookup"><span data-stu-id="91e29-211">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="91e29-212">Nastavte **velikost** vlastnost `315, 600`.</span><span class="sxs-lookup"><span data-stu-id="91e29-212">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="91e29-213">V **zdroje dat** okno, rozbalte **zákazníci** tabulky uzel a vyberte uzel podrobností pro **objednávky** tabulky.</span><span class="sxs-lookup"><span data-stu-id="91e29-213">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="91e29-214">Změňte typ tohoto **objednávky** tabulky Podrobnosti o kliknutím **podrobnosti** v rozevíracím seznamu na uzlu tabulky.</span><span class="sxs-lookup"><span data-stu-id="91e29-214">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="91e29-215">Přetáhněte to **objednávky** uzlu tabulky na oblast šablony položky (horní oblasti) druhého <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-215">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="91e29-216">**OrdersBindingSource** součásti a **OrdersTableAdapter** součásti jsou přidány do komponent.</span><span class="sxs-lookup"><span data-stu-id="91e29-216">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="91e29-217">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="91e29-217">Press F5 to run the application.</span></span> <span data-ttu-id="91e29-218">Když vyberete každého zákazníka v prvním <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit, objednávky tohoto zákazníka jsou zobrazeny ve druhém <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91e29-218">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e29-219">Viz také</span><span class="sxs-lookup"><span data-stu-id="91e29-219">See Also</span></span>  
 [<span data-ttu-id="91e29-220">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-220">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="91e29-221">Postupy: zobrazení vázaných dat v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-221">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="91e29-222">Postupy: zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-222">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="91e29-223">Postupy: Změna rozložení ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-223">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="91e29-224">Postupy: zobrazení položek záhlaví v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-224">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="91e29-225">Postupy: vyhledávání dat v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-225">How to: Search Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="91e29-226">Postupy: vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="91e29-226">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="91e29-227">Postupy: Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-227">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="91e29-228">Postupy: zákaz přidávání a odstraňování položek DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-228">How to: Disable Adding and Deleting DataRepeater Items</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [<span data-ttu-id="91e29-229">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="91e29-229">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
