---
title: Formátování ovládacího prvku DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
ms.openlocfilehash: 30342a89f3176255fa7217ccbbbd91c166ff7f35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732956"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="99ca9-102">Postupy: Formátování ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="99ca9-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="99ca9-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="99ca9-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="99ca9-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="99ca9-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="99ca9-105">Použití různých barev u různých částí <xref:System.Windows.Forms.DataGrid>ho ovládacího prvku může pomáhat usnadnit čtení a interpretaci informací.</span><span class="sxs-lookup"><span data-stu-id="99ca9-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="99ca9-106">Barvu lze použít u řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="99ca9-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="99ca9-107">Řádky a sloupce můžete také skrýt nebo zobrazit podle vašeho uvážení.</span><span class="sxs-lookup"><span data-stu-id="99ca9-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="99ca9-108">Existují tři základní aspekty formátování ovládacího prvku <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="99ca9-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="99ca9-109">Můžete nastavit vlastnosti pro vytvoření výchozího stylu, ve kterém jsou zobrazena data.</span><span class="sxs-lookup"><span data-stu-id="99ca9-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="99ca9-110">Z této základny pak můžete přizpůsobit způsob, jakým jsou v době běhu zobrazeny určité tabulky.</span><span class="sxs-lookup"><span data-stu-id="99ca9-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="99ca9-111">Nakonec můžete upravit, které sloupce se zobrazí v datové mřížce, a také barvy a jiné zobrazené formátování.</span><span class="sxs-lookup"><span data-stu-id="99ca9-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="99ca9-112">Jako počáteční krok při formátování datové mřížky můžete nastavit vlastnosti samotného <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="99ca9-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="99ca9-113">Volby barev a formátů tvoří základ, ze kterého pak můžete provádět změny v závislosti na zobrazených tabulkách dat a sloupcích.</span><span class="sxs-lookup"><span data-stu-id="99ca9-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="99ca9-114">Vytvoření výchozího stylu pro ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="99ca9-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="99ca9-115">Podle potřeby nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="99ca9-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="99ca9-116">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="99ca9-116">Property</span></span>|<span data-ttu-id="99ca9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="99ca9-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="99ca9-118">Vlastnost <xref:System.Windows.Forms.DataGrid.BackColor%2A> definuje barvu sudého číslování řádků mřížky.</span><span class="sxs-lookup"><span data-stu-id="99ca9-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="99ca9-119">Když nastavíte vlastnost <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na jinou barvu, každý další řádek je nastaven na tuto novou barvu (řádky 1, 3, 5 atd.).</span><span class="sxs-lookup"><span data-stu-id="99ca9-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="99ca9-120">Barva pozadí sudého číslování řádků mřížky (řádky 0, 2, 4, 6 a tak dále).</span><span class="sxs-lookup"><span data-stu-id="99ca9-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="99ca9-121">Vzhledem k tomu, že vlastnosti <xref:System.Windows.Forms.DataGrid.BackColor%2A> a <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> určují barvu řádků v mřížce, vlastnost <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> Určuje barvu oblasti nonrow, která je viditelná pouze v případě, že se mřížka posouvá do dolní části, nebo pokud je v mřížce obsažen pouze pár řádků.</span><span class="sxs-lookup"><span data-stu-id="99ca9-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="99ca9-122">Styl ohraničení mřížky, jedna z hodnot <xref:System.Windows.Forms.BorderStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="99ca9-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="99ca9-123">Barva pozadí nadpisu okna mřížky, která se zobrazuje hned nad mřížkou</span><span class="sxs-lookup"><span data-stu-id="99ca9-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="99ca9-124">Písmo popisku v horní části mřížky</span><span class="sxs-lookup"><span data-stu-id="99ca9-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="99ca9-125">Barva pozadí nadpisu okna mřížky</span><span class="sxs-lookup"><span data-stu-id="99ca9-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="99ca9-126">Písmo použité k zobrazení textu v mřížce</span><span class="sxs-lookup"><span data-stu-id="99ca9-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="99ca9-127">Barva písma zobrazeného v datech v řádcích datové mřížky</span><span class="sxs-lookup"><span data-stu-id="99ca9-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="99ca9-128">Barva čar mřížky pro datovou mřížku.</span><span class="sxs-lookup"><span data-stu-id="99ca9-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="99ca9-129">Styl čar, který odděluje buňky mřížky, jednu z hodnot výčtu <xref:System.Windows.Forms.DataGridLineStyle>.</span><span class="sxs-lookup"><span data-stu-id="99ca9-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="99ca9-130">Barva pozadí záhlaví řádků a sloupců</span><span class="sxs-lookup"><span data-stu-id="99ca9-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="99ca9-131">Písmo použité pro záhlaví sloupců</span><span class="sxs-lookup"><span data-stu-id="99ca9-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="99ca9-132">Barva popředí záhlaví sloupců v mřížce, včetně textu záhlaví sloupce a glyfů plus/mínus (pro rozbalení řádků při zobrazení více souvisejících tabulek).</span><span class="sxs-lookup"><span data-stu-id="99ca9-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="99ca9-133">Barva textu všech odkazů v mřížce dat, včetně odkazů na podřízené tabulky, název vztahu atd.</span><span class="sxs-lookup"><span data-stu-id="99ca9-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="99ca9-134">V podřízené tabulce se jedná o barvu pozadí nadřazených řádků.</span><span class="sxs-lookup"><span data-stu-id="99ca9-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="99ca9-135">V podřízené tabulce je to barva popředí nadřazených řádků.</span><span class="sxs-lookup"><span data-stu-id="99ca9-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="99ca9-136">Určuje, zda jsou názvy tabulek a sloupců zobrazeny v nadřazeném řádku prostřednictvím výčtu <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>.</span><span class="sxs-lookup"><span data-stu-id="99ca9-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="99ca9-137">Výchozí šířka (v pixelech) sloupců v mřížce.</span><span class="sxs-lookup"><span data-stu-id="99ca9-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="99ca9-138">Tuto vlastnost nastavte před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastností (buď samostatně, nebo prostřednictvím metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>), nebo vlastnost nebude mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="99ca9-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="99ca9-139">Vlastnost nemůže být nastavena na hodnotu menší než 0.</span><span class="sxs-lookup"><span data-stu-id="99ca9-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="99ca9-140">Výška řádku (v pixelech) řádků v mřížce</span><span class="sxs-lookup"><span data-stu-id="99ca9-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="99ca9-141">Tuto vlastnost nastavte před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastností (buď samostatně, nebo prostřednictvím metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>), nebo vlastnost nebude mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="99ca9-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="99ca9-142">Vlastnost nemůže být nastavena na hodnotu menší než 0.</span><span class="sxs-lookup"><span data-stu-id="99ca9-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="99ca9-143">Šířka záhlaví řádků mřížky</span><span class="sxs-lookup"><span data-stu-id="99ca9-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="99ca9-144">Když je vybrán řádek nebo buňka, jedná se o barvu pozadí.</span><span class="sxs-lookup"><span data-stu-id="99ca9-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="99ca9-145">Když je vybrán řádek nebo buňka, jedná se o barvu popředí.</span><span class="sxs-lookup"><span data-stu-id="99ca9-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="99ca9-146">Mějte na paměti, že při přizpůsobování barev ovládacích prvků je možné nastavit, aby byl ovládací prvek nepřístupný, protože je zvolena špatná barva (například červená a zelená).</span><span class="sxs-lookup"><span data-stu-id="99ca9-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="99ca9-147">K tomuto problému se vyhnete použitím barev dostupných na paletě **systémových barev** .</span><span class="sxs-lookup"><span data-stu-id="99ca9-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="99ca9-148">Následující postupy předpokládají, že ve formuláři je ovládací prvek <xref:System.Windows.Forms.DataGrid> svázaný s datovou tabulkou.</span><span class="sxs-lookup"><span data-stu-id="99ca9-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="99ca9-149">Další informace naleznete v tématu [svázání model Windows Forms ovládacího prvku DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="99ca9-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="99ca9-150">Nastavení stylu tabulky a sloupce tabulky dat prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="99ca9-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="99ca9-151">Vytvořte nový styl tabulky a nastavte jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99ca9-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="99ca9-152">Vytvořte styl sloupce a nastavte jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99ca9-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="99ca9-153">Přidejte styl sloupce do kolekce stylů sloupců stylu tabulky.</span><span class="sxs-lookup"><span data-stu-id="99ca9-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="99ca9-154">Přidejte styl tabulky do kolekce stylů tabulek v datové mřížce.</span><span class="sxs-lookup"><span data-stu-id="99ca9-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="99ca9-155">V následujícím příkladu vytvořte instanci nového <xref:System.Windows.Forms.DataGridTableStyle> a nastavte její vlastnost <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>.</span><span class="sxs-lookup"><span data-stu-id="99ca9-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="99ca9-156">Vytvořte novou instanci **GridColumnStyle** a nastavte její **mapování** (a jiné vlastnosti rozložení a zobrazení).</span><span class="sxs-lookup"><span data-stu-id="99ca9-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="99ca9-157">Opakujte kroky 2 až 6 pro každý styl sloupce, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="99ca9-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="99ca9-158">Následující příklad ukazuje, jak je vytvořen <xref:System.Windows.Forms.DataGridTextBoxColumn>, protože název se zobrazí ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="99ca9-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="99ca9-159">Navíc můžete přidat styl sloupce do <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabulky a přidat styl tabulky do <xref:System.Windows.Forms.GridTableStylesCollection> datové mřížky.</span><span class="sxs-lookup"><span data-stu-id="99ca9-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName   
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName   
       ' to the name of a DataColumn in the DataTable.   
       ' Set the HeaderText and Width properties.   
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to   
       ' the GridTableStylesCollection.   
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName   
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName   
       // to the name of a DataColumn in the DataTable.   
       // Set the HeaderText and Width properties.   
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to   
       // the GridTableStylesCollection.   
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName   
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName   
          // to the name of a DataColumn in the DataTable.   
          // Set the HeaderText and Width properties.   
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to   
          // the GridTableStylesCollection.   
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="99ca9-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="99ca9-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="99ca9-161">Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="99ca9-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="99ca9-162">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="99ca9-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
