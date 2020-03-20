---
title: Formát ovládacího prvku datové mřížky
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
ms.openlocfilehash: 180f837c7d60f49af880faefc05da262be061d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182138"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="82aa4-102">Postupy: Formátování ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="82aa4-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="82aa4-103">Ovládací <xref:System.Windows.Forms.DataGridView> prvek nahradí a přidá <xref:System.Windows.Forms.DataGrid> funkce ovládacího prvku; <xref:System.Windows.Forms.DataGrid> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="82aa4-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="82aa4-104">Další informace naleznete v [tématu Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="82aa4-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="82aa4-105">Použití různých barev na <xref:System.Windows.Forms.DataGrid> různé části ovládacího prvku může usnadnit čtení a interpretaci informací v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="82aa4-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="82aa4-106">Barvu lze aplikovat na řádky a sloupce.</span><span class="sxs-lookup"><span data-stu-id="82aa4-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="82aa4-107">Řádky a sloupce mohou být také skryté nebo zobrazeny podle vašeho uvážení.</span><span class="sxs-lookup"><span data-stu-id="82aa4-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="82aa4-108">Existují tři základní aspekty formátování <xref:System.Windows.Forms.DataGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="82aa4-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="82aa4-109">Můžete nastavit vlastnosti pro vytvoření výchozího stylu, ve kterém jsou data zobrazena.</span><span class="sxs-lookup"><span data-stu-id="82aa4-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="82aa4-110">Z této základny pak můžete přizpůsobit způsob, jakým jsou některé tabulky zobrazeny za běhu.</span><span class="sxs-lookup"><span data-stu-id="82aa4-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="82aa4-111">Nakonec můžete upravit, které sloupce jsou zobrazeny v datové mřížce, stejně jako barvy a další formátování, které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="82aa4-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="82aa4-112">Jako první krok při formátování datové mřížky můžete nastavit <xref:System.Windows.Forms.DataGrid> vlastnosti samotného.</span><span class="sxs-lookup"><span data-stu-id="82aa4-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="82aa4-113">Tyto volby barev a formátů tvoří základ, ze kterého pak můžete provádět změny v závislosti na zobrazených datových tabulkách a sloupcích.</span><span class="sxs-lookup"><span data-stu-id="82aa4-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="82aa4-114">Vytvoření výchozího stylu ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="82aa4-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="82aa4-115">Podle potřeby nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="82aa4-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="82aa4-116">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="82aa4-116">Property</span></span>|<span data-ttu-id="82aa4-117">Popis</span><span class="sxs-lookup"><span data-stu-id="82aa4-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="82aa4-118">Vlastnost <xref:System.Windows.Forms.DataGrid.BackColor%2A> definuje barvu sudých řádků mřížky.</span><span class="sxs-lookup"><span data-stu-id="82aa4-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="82aa4-119">Když nastavíte <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> vlastnost na jinou barvu, každý druhý řádek je nastaven na tuto novou barvu (řádky 1, 3, 5 a tak dále).</span><span class="sxs-lookup"><span data-stu-id="82aa4-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="82aa4-120">Barva pozadí sudých řádků mřížky (řádky 0, 2, 4, 6 a tak dále).</span><span class="sxs-lookup"><span data-stu-id="82aa4-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="82aa4-121">Vzhledem <xref:System.Windows.Forms.DataGrid.BackColor%2A> k <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> tomu, vlastnosti a určuje barvu <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> řádků v mřížce, vlastnost určuje barvu oblasti nonrow, která je viditelná pouze při posunu mřížky dolů, nebo pokud jsou obsaženy pouze několik řádků v mřížce.</span><span class="sxs-lookup"><span data-stu-id="82aa4-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="82aa4-122">Styl ohraničení mřížky, jedna <xref:System.Windows.Forms.BorderStyle> z hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="82aa4-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="82aa4-123">Barva pozadí titulku okna mřížky, která se zobrazí bezprostředně nad mřížkou.</span><span class="sxs-lookup"><span data-stu-id="82aa4-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="82aa4-124">Písmo titulku v horní části mřížky.</span><span class="sxs-lookup"><span data-stu-id="82aa4-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="82aa4-125">Barva pozadí titulku okna mřížky.</span><span class="sxs-lookup"><span data-stu-id="82aa4-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="82aa4-126">Písmo použité k zobrazení textu v mřížce.</span><span class="sxs-lookup"><span data-stu-id="82aa4-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="82aa4-127">Barva písma zobrazená daty v řádcích mřížky dat.</span><span class="sxs-lookup"><span data-stu-id="82aa4-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="82aa4-128">Barva čar mřížky datové mřížky.</span><span class="sxs-lookup"><span data-stu-id="82aa4-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="82aa4-129">Styl čar oddělujících buňky mřížky, <xref:System.Windows.Forms.DataGridLineStyle> jednu z hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="82aa4-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="82aa4-130">Barva pozadí záhlaví řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="82aa4-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="82aa4-131">Písmo použité pro záhlaví sloupců.</span><span class="sxs-lookup"><span data-stu-id="82aa4-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="82aa4-132">Barva popředí záhlaví sloupců mřížky, včetně textu záhlaví sloupce a glyfů plus/mínus (chcete-li rozbalit řádky při zobrazení více souvisejících tabulek).</span><span class="sxs-lookup"><span data-stu-id="82aa4-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="82aa4-133">Barva textu všech odkazů v datové mřížce, včetně odkazů na podřízené tabulky, název vztahu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="82aa4-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="82aa4-134">V podřízené tabulce se jedná o barvu pozadí nadřazených řádků.</span><span class="sxs-lookup"><span data-stu-id="82aa4-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="82aa4-135">V podřízené tabulce se jedná o barvu popředí nadřazených řádků.</span><span class="sxs-lookup"><span data-stu-id="82aa4-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="82aa4-136">Určuje, zda jsou názvy tabulek a sloupců zobrazeny <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> v nadřazeném řádku pomocí výčtu.</span><span class="sxs-lookup"><span data-stu-id="82aa4-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="82aa4-137">Výchozí šířka (v obrazových bodech) sloupců v mřížce.</span><span class="sxs-lookup"><span data-stu-id="82aa4-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="82aa4-138">Nastavte tuto vlastnost před <xref:System.Windows.Forms.DataGrid.DataSource%2A> <xref:System.Windows.Forms.DataGrid.DataMember%2A> resetováním vlastností a <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (samostatně nebo metodou) nebo vlastnost nebude mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="82aa4-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="82aa4-139">Vlastnost nelze nastavit na hodnotu menší než 0.</span><span class="sxs-lookup"><span data-stu-id="82aa4-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="82aa4-140">Výška řádku (v obrazových bodech) řádků v mřížce.</span><span class="sxs-lookup"><span data-stu-id="82aa4-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="82aa4-141">Nastavte tuto vlastnost před <xref:System.Windows.Forms.DataGrid.DataSource%2A> <xref:System.Windows.Forms.DataGrid.DataMember%2A> resetováním vlastností a <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (samostatně nebo metodou) nebo vlastnost nebude mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="82aa4-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="82aa4-142">Vlastnost nelze nastavit na hodnotu menší než 0.</span><span class="sxs-lookup"><span data-stu-id="82aa4-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="82aa4-143">Šířka záhlaví řádků mřížky.</span><span class="sxs-lookup"><span data-stu-id="82aa4-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="82aa4-144">Když je vybrán řádek nebo buňka, jedná se o barvu pozadí.</span><span class="sxs-lookup"><span data-stu-id="82aa4-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="82aa4-145">Když je vybrán řádek nebo buňka, jedná se o barvu popředí.</span><span class="sxs-lookup"><span data-stu-id="82aa4-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="82aa4-146">Mějte na paměti, při přizpůsobení barev ovládacích prvků, že je možné, aby ovládací prvek nepřístupný, z důvodu špatné volby barev (například červené a zelené).</span><span class="sxs-lookup"><span data-stu-id="82aa4-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="82aa4-147">Použijte barvy dostupné na paletě Systémové barvy, abyste se tomuto problému **vyhnuli.**</span><span class="sxs-lookup"><span data-stu-id="82aa4-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="82aa4-148">Následující postupy předpokládají, že <xref:System.Windows.Forms.DataGrid> formulář má ovládací prvek vázaný na tabulku dat.</span><span class="sxs-lookup"><span data-stu-id="82aa4-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="82aa4-149">Další informace naleznete [v tématu Vazba ovládacího prvku Windows Forms DataGrid na zdroj dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="82aa4-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="82aa4-150">Programové nastavení stylu tabulky a sloupce tabulky dat</span><span class="sxs-lookup"><span data-stu-id="82aa4-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="82aa4-151">Vytvořte nový styl tabulky a nastavte jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="82aa4-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="82aa4-152">Vytvořte styl sloupce a nastavte jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="82aa4-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="82aa4-153">Přidejte styl sloupce do kolekce stylů sloupců stylu tabulky.</span><span class="sxs-lookup"><span data-stu-id="82aa4-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="82aa4-154">Přidejte styl tabulky do kolekce stylů tabulek v tabulce mřížky dat.</span><span class="sxs-lookup"><span data-stu-id="82aa4-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="82aa4-155">V níže uvedeném příkladu vytvořte instanci nové <xref:System.Windows.Forms.DataGridTableStyle> a nastavte její <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="82aa4-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="82aa4-156">Vytvořte novou instanci **GridColumnStyle** a nastavte jeho **MappingName** (a některé další vlastnosti rozložení a zobrazení).</span><span class="sxs-lookup"><span data-stu-id="82aa4-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="82aa4-157">Opakujte kroky 2 až 6 pro každý styl sloupce, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="82aa4-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="82aa4-158">Následující příklad ukazuje, <xref:System.Windows.Forms.DataGridTextBoxColumn> jak je vytvořen, protože název má být zobrazen ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="82aa4-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="82aa4-159">Kromě toho přidáte styl sloupce <xref:System.Windows.Forms.GridColumnStylesCollection> do stylu tabulky a přidáte styl tabulky <xref:System.Windows.Forms.GridTableStylesCollection> do mřížky dat.</span><span class="sxs-lookup"><span data-stu-id="82aa4-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82aa4-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="82aa4-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="82aa4-161">Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="82aa4-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="82aa4-162">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="82aa4-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
