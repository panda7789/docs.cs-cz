---
title: 'Návod: Zobrazení dat v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: 8e64a819e9670a29e97140a32c81f5ff9006f83e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388549"
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="50947-102">Návod: Zobrazení dat v ovládacím prvku DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="50947-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="50947-103">Tento názorný postup obsahuje základní zahájení dokončení scénář pro zobrazení vázaných dat v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="50947-104">Předpoklad</span><span class="sxs-lookup"><span data-stu-id="50947-104">Prerequisite</span></span>  
 <span data-ttu-id="50947-105">Tento návod vyžaduje ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="50947-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="50947-106">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="50947-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="50947-107">Pokyny najdete v tématu [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="50947-107">For instructions, see [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="50947-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="50947-108">Overview</span></span>  
 <span data-ttu-id="50947-109">První část tohoto návodu skládá ze čtyř hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="50947-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="50947-110">Vytvoření řešení.</span><span class="sxs-lookup"><span data-stu-id="50947-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="50947-111">Přidání <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="50947-112">Přidání zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="50947-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="50947-113">Přidání ovládacích prvků vázaných na data.</span><span class="sxs-lookup"><span data-stu-id="50947-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="50947-114">Vytvoření řešení DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="50947-115">V prvním kroku vytvoříte projekt a řešení.</span><span class="sxs-lookup"><span data-stu-id="50947-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="50947-116">Chcete-li vytvořit řešení DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="50947-117">V sadě Visual Studio **souboru** nabídky, klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="50947-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="50947-118">V **typy projektů** v podokně **nový projekt** dialogového okna rozbalte **jazyka Visual Basic**a potom klikněte na tlačítko **Windows**.</span><span class="sxs-lookup"><span data-stu-id="50947-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="50947-119">V **šablony** podokně klikněte na tlačítko **formulářová aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="50947-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="50947-120">V **název** zadejte `DataRepeaterApp`.</span><span class="sxs-lookup"><span data-stu-id="50947-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="50947-121">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="50947-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="50947-122">Otevře se Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="50947-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="50947-123">Vyberte formulář v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="50947-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="50947-124">V **vlastnosti** okno, nastaveno **velikost** vlastnost `800, 700`.</span><span class="sxs-lookup"><span data-stu-id="50947-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="50947-125">Přidání ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="50947-126">V tomto kroku přidáte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku na formuláři.</span><span class="sxs-lookup"><span data-stu-id="50947-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="50947-127">Přidání ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="50947-128">Na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="50947-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="50947-129">**Nástrojů** otevře.</span><span class="sxs-lookup"><span data-stu-id="50947-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="50947-130">Vyberte **sady Visual Basic PowerPack** kartu.</span><span class="sxs-lookup"><span data-stu-id="50947-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="50947-131">Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> na ovládací prvek **Form1**.</span><span class="sxs-lookup"><span data-stu-id="50947-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="50947-132">V okně Vlastnosti nastavte **umístění** vlastnost `0, 25`.</span><span class="sxs-lookup"><span data-stu-id="50947-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="50947-133">Nastavte **velikost** vlastnost `460, 600`.</span><span class="sxs-lookup"><span data-stu-id="50947-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="50947-134">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="50947-134">Adding a Data Source</span></span>  
 <span data-ttu-id="50947-135">V tomto kroku přidáte zdroj dat pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="50947-136">Chcete-li přidat zdroj dat</span><span class="sxs-lookup"><span data-stu-id="50947-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="50947-137">Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.</span><span class="sxs-lookup"><span data-stu-id="50947-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="50947-138">V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.</span><span class="sxs-lookup"><span data-stu-id="50947-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="50947-139">Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="50947-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="50947-140">Na **vyberte datové připojení** stránce, proveďte jednu z následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="50947-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="50947-141">Pokud připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, klikněte na něj.</span><span class="sxs-lookup"><span data-stu-id="50947-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="50947-142">-nebo-</span><span class="sxs-lookup"><span data-stu-id="50947-142">-or-</span></span>  
  
    -   <span data-ttu-id="50947-143">Klikněte na tlačítko **nové připojení** konfigurace nové datové připojení.</span><span class="sxs-lookup"><span data-stu-id="50947-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="50947-144">Další informace najdete v tématu [přidat nové připojení](/visualstudio/data-tools/add-new-connections).</span><span class="sxs-lookup"><span data-stu-id="50947-144">For more information, see [Add new connections](/visualstudio/data-tools/add-new-connections).</span></span>  
  
5.  <span data-ttu-id="50947-145">Pokud databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="50947-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50947-146">Pokud se zobrazí dialogové okno, klikněte na tlačítko **Ano** k uložení souboru do projektu.</span><span class="sxs-lookup"><span data-stu-id="50947-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="50947-147">Klikněte na tlačítko **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.</span><span class="sxs-lookup"><span data-stu-id="50947-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="50947-148">Rozbalte **tabulky** uzlu **zvolte vaše databázové objekty** stránky.</span><span class="sxs-lookup"><span data-stu-id="50947-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="50947-149">Zaškrtněte políčka vedle položky **zákazníkům** a **objednávky** tabulky a pak klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="50947-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="50947-150">**NorthwindDataSet** se přidá do vašeho projektu a **zákazníkům** a **objednávky** tabulky se zobrazí v **zdroje dat** okna.</span><span class="sxs-lookup"><span data-stu-id="50947-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="50947-151">Přidání ovládacích prvků vázaných na Data</span><span class="sxs-lookup"><span data-stu-id="50947-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="50947-152">V tomto kroku přidáte ovládací prvky vázané na data <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="50947-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="50947-153">Přidání ovládacích prvků vázaných na data</span><span class="sxs-lookup"><span data-stu-id="50947-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="50947-154">V **zdroje dat** okno, vyberte uzel nejvyšší úrovně **zákazníkům** tabulky.</span><span class="sxs-lookup"><span data-stu-id="50947-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="50947-155">Změňte typ přetažení tabulky **podrobnosti** kliknutím **podrobnosti** v rozevíracím seznamu na uzel tabulky.</span><span class="sxs-lookup"><span data-stu-id="50947-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="50947-156">Vyberte **zákazníkům** tabulky uzlu a přetáhněte ji na šablonu oblast položky (horní oblasti) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="50947-157">A <xref:System.Windows.Forms.BindingNavigator> ovládací prvek je přidán do formuláře a **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, a **CustomersBindingNavigator** součásti jsou přidány do panelu komponent.</span><span class="sxs-lookup"><span data-stu-id="50947-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="50947-158">Vyberte všechny pole a jejich přidružené popisky a umístit je u levého okraje oblasti šablony položek.</span><span class="sxs-lookup"><span data-stu-id="50947-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="50947-159">Vyberte posledních pět polí (**oblasti**, **PSČ**, **země**, **Phone**, a **Fax**) a jejich přidružené popisky a je přesunout nahoru a napravo od prvních šest polí.</span><span class="sxs-lookup"><span data-stu-id="50947-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="50947-160">Vyberte šablonu položky (horní oblasti ovládacího prvku).</span><span class="sxs-lookup"><span data-stu-id="50947-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="50947-161">V okně Vlastnosti nastavte **velikost** vlastnost `427, 170`.</span><span class="sxs-lookup"><span data-stu-id="50947-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="50947-162">V tomto okamžiku máte funkční aplikaci, která se zobrazí s opakováním seznam zákazníků.</span><span class="sxs-lookup"><span data-stu-id="50947-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="50947-163">Stisknutím klávesy F5 spusťte aplikaci, změnit data a přidat nebo odstranit záznamy o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="50947-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="50947-164">V dalším volitelným krokům, se dozvíte, jak přizpůsobit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="50947-165">Další kroky (volitelné)</span><span class="sxs-lookup"><span data-stu-id="50947-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="50947-166">Tato část návodu se skládá ze čtyř volitelné kroky:</span><span class="sxs-lookup"><span data-stu-id="50947-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="50947-167">Změna vzhledu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="50947-168">Zabránění uživatelům v přidávání nebo odstraňování záznamů.</span><span class="sxs-lookup"><span data-stu-id="50947-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="50947-169">Přidání schopností vyhledávání do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="50947-170">Přidat tabulku do seznamu a podrobností <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="50947-171">Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="50947-172">V tomto volitelný krok, můžete změnit `BackColor` z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="50947-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="50947-173">Je také přidat kód k zobrazení řádků v střídavých barvy a změnit popisku `ForeColor` podmíněně.</span><span class="sxs-lookup"><span data-stu-id="50947-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="50947-174">Chcete-li změnit vzhled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="50947-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="50947-175">V Návrháři formulářů Windows vyberte hlavní oblast (nižší) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="50947-176">V okně Vlastnosti nastavte `BackColor` vlastnost na bílou.</span><span class="sxs-lookup"><span data-stu-id="50947-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="50947-177">Dvakrát klikněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="50947-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="50947-178">V editoru kódu, v případě rozevíracího seznamu, klikněte na tlačítko **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="50947-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="50947-179">V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužná rutina události, přidejte následující kód do alternativní `BackColor`:</span><span class="sxs-lookup"><span data-stu-id="50947-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  <span data-ttu-id="50947-180">V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužná rutina události, přidejte následující kód pro změnu `ForeColor` popisku v závislosti na podmínku:</span><span class="sxs-lookup"><span data-stu-id="50947-180">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  <span data-ttu-id="50947-181">Stisknutím klávesy F5 spusťte aplikaci a zobrazit vlastní nastavení.</span><span class="sxs-lookup"><span data-stu-id="50947-181">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="50947-182">Zabránění uživatelům v přidávání nebo odstraňování záznamů</span><span class="sxs-lookup"><span data-stu-id="50947-182">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="50947-183">V tomto volitelném kroku přidáte kód, který zabrání uživatelům v přidávání nebo odstraňování záznamů v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-183">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="50947-184">Chcete-li zabránit uživatelům v přidávání a odstraňování záznamů</span><span class="sxs-lookup"><span data-stu-id="50947-184">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="50947-185">V Návrháři formulářů Windows klikněte dvakrát na formuláři se otevřít Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="50947-185">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="50947-186">Přidejte následující kód, který `Form_Load` události:</span><span class="sxs-lookup"><span data-stu-id="50947-186">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  <span data-ttu-id="50947-187">V rozevíracím seznamu názvu třídy, klikněte na tlačítko **BindingNavigatorDeleteItem**.</span><span class="sxs-lookup"><span data-stu-id="50947-187">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="50947-188">V rozevíracím seznamu název metody, klikněte na tlačítko **EnabledChanged**.</span><span class="sxs-lookup"><span data-stu-id="50947-188">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="50947-189">Přidejte následující kód, který `BindingNavigatorDeleteItem_EnabledChanged` obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="50947-189">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="50947-190">Tento krok je nezbytný, protože <xref:System.Windows.Forms.BindingSource> vám umožní **DeleteItem** tlačítko pokaždé, když se změní aktuální záznam.</span><span class="sxs-lookup"><span data-stu-id="50947-190">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="50947-191">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="50947-191">Press F5 to run the application.</span></span> <span data-ttu-id="50947-192">Všimněte si, **DeleteItem** je tlačítko neaktivní a nelze odstranit položky, stisknutím klávesy DELETE.</span><span class="sxs-lookup"><span data-stu-id="50947-192">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="50947-193">Přidání schopností vyhledávání do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-193">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="50947-194">V tomto kroku volitelné implementace umožňuje najít hodnotu v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-194">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="50947-195">Pokud se řetězec najde, vybere ovládací prvek položky, který obsahuje hodnotu a položce se posune do zobrazení.</span><span class="sxs-lookup"><span data-stu-id="50947-195">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="50947-196">Můžete přidat možnosti vyhledávání</span><span class="sxs-lookup"><span data-stu-id="50947-196">To add search capability</span></span>  
  
1.  <span data-ttu-id="50947-197">Přetáhněte <xref:System.Windows.Forms.TextBox> ovládacího prvku **nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-197">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="50947-198">Přesuňte ho pod <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-198">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="50947-199">V okně Vlastnosti změňte **název** vlastnost **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="50947-199">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="50947-200">Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-200">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="50947-201">Přesuňte ho pod <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-201">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="50947-202">V okně Vlastnosti změňte **název** vlastnost **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="50947-202">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="50947-203">Změnit **Text** vlastnost **hledání**.</span><span class="sxs-lookup"><span data-stu-id="50947-203">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="50947-204">Dvakrát klikněte <xref:System.Windows.Forms.Button> ovládací prvek, otevře se Editor kódu a přidejte následující kód, který `SearchButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="50947-204">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  <span data-ttu-id="50947-205">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="50947-205">Press F5 to run the application.</span></span> <span data-ttu-id="50947-206">Zadejte ID zákazníka v **SearchTextBox** a klikněte na tlačítko **hledání** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="50947-206">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="50947-207">Přidání do ovládacího prvku DateRepeater. hlavní a tabulka podrobností</span><span class="sxs-lookup"><span data-stu-id="50947-207">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="50947-208">V tomto kroku volitelné přidejte druhý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek zobrazí související objednávky pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="50947-208">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="50947-209">Chcete-li přidat tabulku a podrobností</span><span class="sxs-lookup"><span data-stu-id="50947-209">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="50947-210">Přetáhněte druhý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="50947-210">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="50947-211">V okně Vlastnosti nastavte **umístění** vlastnost `465, 25`.</span><span class="sxs-lookup"><span data-stu-id="50947-211">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="50947-212">Nastavte **velikost** vlastnost `315, 600`.</span><span class="sxs-lookup"><span data-stu-id="50947-212">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="50947-213">V **zdroje dat** okna, rozbalte **zákazníkům** tabulky uzlů a vyberte uzel podrobností pro **objednávky** tabulky.</span><span class="sxs-lookup"><span data-stu-id="50947-213">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="50947-214">Změňte typ přetažení tohoto objektu **objednávky** tabulky Podrobnosti kliknutím **podrobnosti** v rozevíracím seznamu na uzel tabulky.</span><span class="sxs-lookup"><span data-stu-id="50947-214">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="50947-215">Přetáhněte toto **objednávky** uzel tabulky na oblast šablony položky (horní oblasti) druhého <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-215">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="50947-216">**OrdersBindingSource** komponenty a **OrdersTableAdapter** součásti jsou přidány do panelu komponent.</span><span class="sxs-lookup"><span data-stu-id="50947-216">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="50947-217">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="50947-217">Press F5 to run the application.</span></span> <span data-ttu-id="50947-218">Když vyberete každého zákazníka v prvním <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit, objednávky daného zákazníka se zobrazí v druhé <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50947-218">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50947-219">Viz také</span><span class="sxs-lookup"><span data-stu-id="50947-219">See Also</span></span>  
 [<span data-ttu-id="50947-220">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-220">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="50947-221">Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-221">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="50947-222">Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-222">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="50947-223">Postupy: Změna rozložení ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-223">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="50947-224">Postupy: Zobrazení záhlaví položek v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-224">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="50947-225">Postupy: Vyhledávání dat v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-225">How to: Search Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="50947-226">Postupy: vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="50947-226">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="50947-227">Postupy: Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-227">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="50947-228">Postupy: Zákaz přidávání a odstraňování položek DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-228">How to: Disable Adding and Deleting DataRepeater Items</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [<span data-ttu-id="50947-229">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="50947-229">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
