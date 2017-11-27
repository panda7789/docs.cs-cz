---
title: "Postupy: Formátování ovládacího prvku Windows Forms DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8518fdcaca7ebed65d0923b9bc1fe1a6797b97c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="dd7c5-102">Postupy: Formátování ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="dd7c5-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="dd7c5-103"><xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="dd7c5-104">Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="dd7c5-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="dd7c5-105">Použití různých barev pro různé součásti <xref:System.Windows.Forms.DataGrid> řízení může pomoct snadněji informace v něm ke čtení a interpretovat.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="dd7c5-106">Barva je použít pro řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="dd7c5-107">Řádků a sloupců, můžete také být skrytý nebo vidět svého uvážení.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="dd7c5-108">Existují tři základní aspekty formátování <xref:System.Windows.Forms.DataGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="dd7c5-109">Můžete nastavit vlastnosti pro vytvoření výchozí styl, ve kterém se zobrazí data.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="dd7c5-110">Z tohoto základní následně můžete přizpůsobit způsob zobrazování určité tabulky v době běhu.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="dd7c5-111">Nakonec můžete upravit sloupce, které se zobrazují v datové mřížce, jakož i barvy a další formátování, které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="dd7c5-112">Jako počáteční krok při formátování dat mřížky, můžete nastavit vlastnosti <xref:System.Windows.Forms.DataGrid> sám sebe.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="dd7c5-113">Tyto možnosti barvy a formát tvoří základ, ze které potom můžete provést změny v závislosti na data tabulky a sloupce zobrazí.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="dd7c5-114">Pro vytvoření výchozí styl ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="dd7c5-114">To establish a default style for the DataGrid control</span></span>  
  
1.  <span data-ttu-id="dd7c5-115">Podle potřeby nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="dd7c5-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="dd7c5-116">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="dd7c5-116">Property</span></span>|<span data-ttu-id="dd7c5-117">Popis</span><span class="sxs-lookup"><span data-stu-id="dd7c5-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="dd7c5-118"><xref:System.Windows.Forms.DataGrid.BackColor%2A> Vlastnost definuje barvu sudých řádků mřížky.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="dd7c5-119">Když nastavíte <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na jinou barvu, každý druhý řádek je nastavena na tuto novou barvu (řádků 1, 3, 5 a tak dále).</span><span class="sxs-lookup"><span data-stu-id="dd7c5-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="dd7c5-120">Barva pozadí sudých řádků mřížky (řádků 0, 2, 4, 6 a tak dále).</span><span class="sxs-lookup"><span data-stu-id="dd7c5-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="dd7c5-121">Zatímco <xref:System.Windows.Forms.DataGrid.BackColor%2A> a <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> vlastnosti určuje barvu řádků v mřížce <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> vlastnost určuje barvu nonrow oblast, která je viditelná jen při přesunut do dolní oblasti mřížky, nebo pokud jenom pár řádků, které jsou obsaženy v mřížky.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="dd7c5-122">Styl ohraničení mřížky, jeden z <xref:System.Windows.Forms.BorderStyle> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="dd7c5-123">Barva pozadí mřížky okno popisek, který se zobrazí okamžitě nad mřížky.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="dd7c5-124">Písmo popisku v horní části mřížky.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="dd7c5-125">Barva pozadí záhlaví okna mřížky.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="dd7c5-126">Písmo použité k zobrazení textu v mřížce.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="dd7c5-127">Barva písma zobrazuje data v řádky mřížky data.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="dd7c5-128">Barva čar mřížky dat mřížky.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="dd7c5-129">Styl čar oddělujících buňky mřížky, jeden z <xref:System.Windows.Forms.DataGridLineStyle> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="dd7c5-130">Barva pozadí záhlaví řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="dd7c5-131">Písmo použité pro záhlaví sloupců.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="dd7c5-132">Barvu popředí záhlaví sloupců mřížky, včetně textu záhlaví sloupce a glyfy plus nebo minus (Chcete-li rozbalit řádků, pokud se zobrazí více související tabulky).</span><span class="sxs-lookup"><span data-stu-id="dd7c5-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="dd7c5-133">Barva textu všechny odkazy na data mřížky, včetně odkazů na podřízené tabulky, název relace a tak dále.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="dd7c5-134">V podřízené tabulce je to barvu pozadí nadřazených řádků.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="dd7c5-135">V podřízené tabulce je to barvu popředí nadřazených řádků.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="dd7c5-136">Určuje, zda jsou názvy tabulek a sloupců zobrazovat v řádku nadřazené prostřednictvím <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="dd7c5-137">Šířka výchozí sloupců v mřížce (v pixelech).</span><span class="sxs-lookup"><span data-stu-id="dd7c5-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="dd7c5-138">Tuto vlastnost nastavit před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti (buď samostatně, nebo pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), nebo vlastnost nebude mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="dd7c5-139">Vlastnost nelze nastavit na hodnotu menší než 0.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="dd7c5-140">Výška řádku řádků v mřížce (v pixelech).</span><span class="sxs-lookup"><span data-stu-id="dd7c5-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="dd7c5-141">Tuto vlastnost nastavit před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti (buď samostatně, nebo pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), nebo vlastnost nebude mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="dd7c5-142">Vlastnost nelze nastavit na hodnotu menší než 0.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="dd7c5-143">Šířka záhlaví řádků mřížky.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="dd7c5-144">Pokud je vybraný řádek nebo buňky, jde barvu pozadí.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="dd7c5-145">Pokud je vybraný řádek nebo buňky, jde barvu popředí.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="dd7c5-146">Mějte na paměti, když přizpůsobení barev ovládacích prvků, aby bylo možné zajistit ovládacího prvku nepřístupný z důvodu nízký barva výběru (například red a zelená).</span><span class="sxs-lookup"><span data-stu-id="dd7c5-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="dd7c5-147">Použít k dispozici na barvy **barvy systému** palety chcete tomuto problému vyhnout.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="dd7c5-148">Následujících postupech se předpokládá má formulář <xref:System.Windows.Forms.DataGrid> ovládací prvek vázán k tabulce data.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="dd7c5-149">Další informace najdete v tématu [Vazba ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="dd7c5-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="dd7c5-150">Chcete-li nastavit styl tabulky a sloupce tabulky dat prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="dd7c5-150">To set the table and column style of a data table programmatically</span></span>  
  
1.  <span data-ttu-id="dd7c5-151">Vytvořte nový styl tabulky a nastavte její vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-151">Create a new table style and set its properties.</span></span>  
  
2.  <span data-ttu-id="dd7c5-152">Vytvořte styl sloupce a nastavte její vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-152">Create a column style and set its properties.</span></span>  
  
3.  <span data-ttu-id="dd7c5-153">Styl tabulky sloupec styly kolekce přidáte styl sloupce.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-153">Add the column style to the table style's column styles collection.</span></span>  
  
4.  <span data-ttu-id="dd7c5-154">Styl tabulky přidáte do kolekce stylů mřížky dat tabulky.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5.  <span data-ttu-id="dd7c5-155">V následujícím příkladu vytvoření instance nového <xref:System.Windows.Forms.DataGridTableStyle> a nastavit jeho <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6.  <span data-ttu-id="dd7c5-156">Vytvořit novou instanci třídy **GridColumnStyle** a nastavit jeho **MappingName** (a některé další vlastnosti rozložení a zobrazení).</span><span class="sxs-lookup"><span data-stu-id="dd7c5-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7.  <span data-ttu-id="dd7c5-157">Opakujte kroky 2 až 6 pro každý sloupec styl, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="dd7c5-158">Následující příklad ukazuje, jak <xref:System.Windows.Forms.DataGridTextBoxColumn> je vytvořit, protože název je zobrazený ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="dd7c5-159">Kromě toho můžete přidat styl sloupec, který se <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabulky a přidejte styl tabulky na <xref:System.Windows.Forms.GridTableStylesCollection> dat mřížky.</span><span class="sxs-lookup"><span data-stu-id="dd7c5-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd7c5-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd7c5-160">See Also</span></span>  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [<span data-ttu-id="dd7c5-161">Postupy: odstranění či skrytí sloupců v systému Windows Forms DataGrid – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="dd7c5-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="dd7c5-162">DataGrid – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="dd7c5-162">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
