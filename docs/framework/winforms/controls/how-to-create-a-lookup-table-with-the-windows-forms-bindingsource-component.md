---
title: Vytvoření vyhledávací tabulky pomocí komponenty BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: ccf2bfa6cf3f56a38b55f8c87004c42a46172891
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736810"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="943e5-102">Postupy: Vytváření vyhledávacích tabulek s komponentou Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="943e5-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="943e5-103">Vyhledávací tabulka je tabulka dat, která má sloupec, který zobrazuje data ze záznamů v tabulce v relaci.</span><span class="sxs-lookup"><span data-stu-id="943e5-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="943e5-104">V následujících postupech se pro zobrazení pole s relací cizího klíče z nadřazeného objektu na podřízenou tabulku používá ovládací prvek <xref:System.Windows.Forms.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="943e5-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="943e5-105">Tady je příklad nadřazené a podřízené tabulky, která vám umožní vizualizovat tyto dvě tabulky a tuto relaci:</span><span class="sxs-lookup"><span data-stu-id="943e5-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="943e5-106">Zákazníci (nadřazená tabulka)</span><span class="sxs-lookup"><span data-stu-id="943e5-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="943e5-107">ID</span><span class="sxs-lookup"><span data-stu-id="943e5-107">CustomerID</span></span>|<span data-ttu-id="943e5-108">customerName</span><span class="sxs-lookup"><span data-stu-id="943e5-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="943e5-109">712</span><span class="sxs-lookup"><span data-stu-id="943e5-109">712</span></span>|<span data-ttu-id="943e5-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="943e5-110">Paul Koch</span></span>|  
|<span data-ttu-id="943e5-111">713</span><span class="sxs-lookup"><span data-stu-id="943e5-111">713</span></span>|<span data-ttu-id="943e5-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="943e5-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="943e5-113">Orders (podřízená tabulka)</span><span class="sxs-lookup"><span data-stu-id="943e5-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="943e5-114">Seskup</span><span class="sxs-lookup"><span data-stu-id="943e5-114">OrderID</span></span>|<span data-ttu-id="943e5-115">OrderDate</span><span class="sxs-lookup"><span data-stu-id="943e5-115">OrderDate</span></span>|<span data-ttu-id="943e5-116">ID</span><span class="sxs-lookup"><span data-stu-id="943e5-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="943e5-117">903</span><span class="sxs-lookup"><span data-stu-id="943e5-117">903</span></span>|<span data-ttu-id="943e5-118">12. února 2004</span><span class="sxs-lookup"><span data-stu-id="943e5-118">February 12, 2004</span></span>|<span data-ttu-id="943e5-119">712</span><span class="sxs-lookup"><span data-stu-id="943e5-119">712</span></span>|  
|<span data-ttu-id="943e5-120">904</span><span class="sxs-lookup"><span data-stu-id="943e5-120">904</span></span>|<span data-ttu-id="943e5-121">13. února 2004</span><span class="sxs-lookup"><span data-stu-id="943e5-121">February 13, 2004</span></span>|<span data-ttu-id="943e5-122">713</span><span class="sxs-lookup"><span data-stu-id="943e5-122">713</span></span>|  
  
 <span data-ttu-id="943e5-123">V tomto scénáři jedna tabulka, zákazníci, ukládá skutečné informace, které chcete zobrazit a uložit.</span><span class="sxs-lookup"><span data-stu-id="943e5-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="943e5-124">Pokud ale chcete ušetřit místo, tabulka opustí data, která zvyšují přehlednost.</span><span class="sxs-lookup"><span data-stu-id="943e5-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="943e5-125">Druhá tabulka, Orders, obsahuje jenom informace o tom, které ID zákazníka jsou ekvivalentní k tomuto datu a ID objednávky.</span><span class="sxs-lookup"><span data-stu-id="943e5-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="943e5-126">Neexistují žádné zmínky o názvech zákazníků.</span><span class="sxs-lookup"><span data-stu-id="943e5-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="943e5-127">V ovládacím prvku [ComboBox](combobox-control-windows-forms.md) jsou nastaveny čtyři důležité vlastnosti pro vytvoření vyhledávací tabulky.</span><span class="sxs-lookup"><span data-stu-id="943e5-127">Four important properties are set on the [ComboBox Control](combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
- <span data-ttu-id="943e5-128">Vlastnost <xref:System.Windows.Forms.ComboBox.DataSource%2A> obsahuje název tabulky.</span><span class="sxs-lookup"><span data-stu-id="943e5-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
- <span data-ttu-id="943e5-129">Vlastnost <xref:System.Windows.Forms.ListControl.DisplayMember%2A> obsahuje datový sloupec této tabulky, který chcete zobrazit pro text ovládacího prvku (jméno zákazníka).</span><span class="sxs-lookup"><span data-stu-id="943e5-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
- <span data-ttu-id="943e5-130">Vlastnost <xref:System.Windows.Forms.ListControl.ValueMember%2A> obsahuje datový sloupec v tabulce s uloženými informacemi (číslo ID v nadřazené tabulce).</span><span class="sxs-lookup"><span data-stu-id="943e5-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
- <span data-ttu-id="943e5-131">Vlastnost <xref:System.Windows.Forms.ListControl.SelectedValue%2A> poskytuje hodnotu vyhledávání pro podřízenou tabulku na základě <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="943e5-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="943e5-132">Níže uvedené postupy vám ukážou, jak rozvrhnout formulář jako vyhledávací tabulku a vytvořit z nich data s ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="943e5-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="943e5-133">Aby bylo možné úspěšně dokončit postupy, musíte mít zdroj dat s nadřazenými a podřízenými tabulkami, které mají relaci cizího klíče, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="943e5-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="943e5-134">Vytvoření uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="943e5-134">To create the user interface</span></span>  
  
1. <span data-ttu-id="943e5-135">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.ComboBox> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="943e5-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="943e5-136">Tento ovládací prvek zobrazí sloupec z nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="943e5-136">This control will display the column from parent table.</span></span>  
  
2. <span data-ttu-id="943e5-137">Přetáhněte další ovládací prvky pro zobrazení podrobností z podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="943e5-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="943e5-138">Formát dat v tabulce by měl určovat, které ovládací prvky si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="943e5-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="943e5-139">Další informace naleznete v tématu [model Windows Forms Controls by Function](windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="943e5-139">For more information, see [Windows Forms Controls by Function](windows-forms-controls-by-function.md).</span></span>  
  
3. <span data-ttu-id="943e5-140">Přetáhněte ovládací prvek <xref:System.Windows.Forms.BindingNavigator> do formuláře. To vám umožní procházet data v podřízené tabulce.</span><span class="sxs-lookup"><span data-stu-id="943e5-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="943e5-141">Připojení k datům a jejich svázání s ovládacími prvky</span><span class="sxs-lookup"><span data-stu-id="943e5-141">To connect to the data and bind it to controls</span></span>  
  
1. <span data-ttu-id="943e5-142">Vyberte <xref:System.Windows.Forms.ComboBox> a kliknutím na Inteligentní panel glyf zobrazíte dialogové okno Inteligentní panel.</span><span class="sxs-lookup"><span data-stu-id="943e5-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2. <span data-ttu-id="943e5-143">Vyberte možnost **použít položky vázané na data**.</span><span class="sxs-lookup"><span data-stu-id="943e5-143">Select **Use data bound items**.</span></span>  
  
3. <span data-ttu-id="943e5-144">Klikněte na šipku vedle rozevíracího seznamu **zdroj dat** .</span><span class="sxs-lookup"><span data-stu-id="943e5-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="943e5-145">Pokud byl zdroj dat dříve nakonfigurován pro projekt nebo formulář, zobrazí se. v opačném případě proveďte následující kroky (Tento příklad používá tabulky Zákazníci a objednávky ukázkové databáze Northwind a odkazuje na ně v závorkách).</span><span class="sxs-lookup"><span data-stu-id="943e5-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1. <span data-ttu-id="943e5-146">Kliknutím na **Přidat zdroj dat projektu** se můžete připojit k datům a vytvořit zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="943e5-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2. <span data-ttu-id="943e5-147">Na úvodní stránce **Průvodce konfigurací zdroje dat** klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="943e5-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3. <span data-ttu-id="943e5-148">Vyberte možnost **databáze** na stránce **Vybrat typ zdroje dat** .</span><span class="sxs-lookup"><span data-stu-id="943e5-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4. <span data-ttu-id="943e5-149">Vyberte datové připojení ze seznamu dostupných připojení na stránce **Vyberte datové připojení** .</span><span class="sxs-lookup"><span data-stu-id="943e5-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="943e5-150">Pokud požadované datové připojení není k dispozici, vyberte **nové připojení** a vytvořte nové datové připojení.</span><span class="sxs-lookup"><span data-stu-id="943e5-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5. <span data-ttu-id="943e5-151">Klikněte na tlačítko **Ano, uložit připojení** pro uložení připojovacího řetězce do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="943e5-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6. <span data-ttu-id="943e5-152">Vyberte databázové objekty, které chcete přenést do aplikace.</span><span class="sxs-lookup"><span data-stu-id="943e5-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="943e5-153">V takovém případě vyberte nadřazenou tabulku a podřízenou tabulku (například zákazníci a objednávky) se vztahem cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="943e5-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7. <span data-ttu-id="943e5-154">Pokud chcete, nahraďte výchozí název datové sady.</span><span class="sxs-lookup"><span data-stu-id="943e5-154">Replace the default dataset name if you want.</span></span>  
  
    8. <span data-ttu-id="943e5-155">Klikněte na **Finish** (Dokončit).</span><span class="sxs-lookup"><span data-stu-id="943e5-155">Click **Finish**.</span></span>  
  
4. <span data-ttu-id="943e5-156">V rozevíracím seznamu **Zobrazit člena** vyberte název sloupce (například kontakt), který se má zobrazit v poli se seznamem.</span><span class="sxs-lookup"><span data-stu-id="943e5-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5. <span data-ttu-id="943e5-157">V rozevíracím seznamu **člen hodnoty** vyberte sloupec (například CustomerID) k provedení operace vyhledávání v podřízené tabulce.</span><span class="sxs-lookup"><span data-stu-id="943e5-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6. <span data-ttu-id="943e5-158">V rozevíracím seznamu **Vybraná hodnota** přejděte na **zdroje dat projektu** a datovou sadu, kterou jste právě vytvořili, která obsahuje nadřazené a podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="943e5-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="943e5-159">Vyberte stejnou vlastnost podřízené tabulky, která je členem hodnoty nadřazené tabulky (například Orders. CustomerID).</span><span class="sxs-lookup"><span data-stu-id="943e5-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="943e5-160">Budou vytvořeny příslušné <xref:System.Windows.Forms.BindingSource>, datové sady a součásti adaptéru tabulky a přidány do formuláře.</span><span class="sxs-lookup"><span data-stu-id="943e5-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7. <span data-ttu-id="943e5-161">Navažte ovládací prvek <xref:System.Windows.Forms.BindingNavigator> na <xref:System.Windows.Forms.BindingSource> podřízené tabulky (například `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="943e5-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8. <span data-ttu-id="943e5-162">Navažte ovládací prvky kromě <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.BindingNavigator> řízení na pole podrobností z <xref:System.Windows.Forms.BindingSource> podřízené tabulky (například `OrdersBindingSource`), kterou chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="943e5-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943e5-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="943e5-163">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="943e5-164">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="943e5-164">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="943e5-165">Ovládací prvek ComboBox</span><span class="sxs-lookup"><span data-stu-id="943e5-165">ComboBox Control</span></span>](combobox-control-windows-forms.md)
- [<span data-ttu-id="943e5-166">Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="943e5-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
