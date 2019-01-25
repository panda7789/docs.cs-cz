---
title: 'Postupy: Formát dat v Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: fa029a46f1553d8d371fd574c21e7a016e7b5500
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598118"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ccb6a-102">Postupy: Formát dat v Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ccb6a-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ccb6a-103">Následující postupy ukazují základní formátování pomocí hodnot v buňkách <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastnost <xref:System.Windows.Forms.DataGridView> ovládacího prvku a konkrétní sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="ccb6a-104">Informace o formátování pokročilé dat najdete v tématu [jak: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ccb6a-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="ccb6a-105">Hodnoty data a formát měny</span><span class="sxs-lookup"><span data-stu-id="ccb6a-105">To format currency and date values</span></span>  
  
-   <span data-ttu-id="ccb6a-106">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="ccb6a-107">Následující příklad kódu nastaví formát pro konkrétní sloupce pomocí <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnost sady sloupců.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="ccb6a-108">Hodnoty v `UnitPrice` sloupce se zobrazí v aktuálním formátu měny specifické pro jazykovou verzi, se zápornými hodnotami uzavřen v závorkách.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="ccb6a-109">Hodnoty v `ShipDate` sloupci se zobrazují ve formátu krátkého formátu data aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="ccb6a-110">Další informace o <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> hodnoty, najdete v článku [Formatting Types](../../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="ccb6a-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="ccb6a-111">Pro přizpůsobení zobrazení hodnot null databáze</span><span class="sxs-lookup"><span data-stu-id="ccb6a-111">To customize the display of null database values</span></span>  
  
-   <span data-ttu-id="ccb6a-112">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="ccb6a-113">Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost pro zobrazení "žádná položka" všechny buňky obsahující hodnoty rovné <xref:System.DBNull.Value?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="ccb6a-114">Chcete-li povolit zalamování řádků v buňkách založený na textu</span><span class="sxs-lookup"><span data-stu-id="ccb6a-114">To enable wordwrap in text-based cells</span></span>  
  
-   <span data-ttu-id="ccb6a-115">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> na některý <xref:System.Windows.Forms.DataGridViewTriState> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="ccb6a-116">Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnosti chcete nastavit režim zalamování řádků pro celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="ccb6a-117">Chcete-li určit zarovnání textu buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="ccb6a-117">To specify the text alignment of DataGridView cells</span></span>  
  
-   <span data-ttu-id="ccb6a-118">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> na některý <xref:System.Windows.Forms.DataGridViewContentAlignment> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="ccb6a-119">Následující příklad kódu nastaví zarovnání pro konkrétní sloupce pomocí <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnost sloupce.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="ccb6a-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccb6a-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ccb6a-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ccb6a-121">Compiling the Code</span></span>  
 <span data-ttu-id="ccb6a-122">Tyto příklady vyžadují:</span><span class="sxs-lookup"><span data-stu-id="ccb6a-122">These examples require:</span></span>  
  
-   <span data-ttu-id="ccb6a-123">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , která obsahuje sloupec s názvem `UnitPrice`, sloupec s názvem `ShipDate`a sloupec s názvem `CustomerName`.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
-   <span data-ttu-id="ccb6a-124">Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ccb6a-125">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ccb6a-125">Robust Programming</span></span>  
 <span data-ttu-id="ccb6a-126">Pro maximální rozšiřitelnost, by měly sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více řádky, sloupce nebo buňky, které používají stejné styly spíše než nastavení vlastnosti stylu pro každý prvek samostatně.</span><span class="sxs-lookup"><span data-stu-id="ccb6a-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="ccb6a-127">Další informace najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ccb6a-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb6a-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccb6a-128">See also</span></span>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="ccb6a-129">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ccb6a-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ccb6a-130">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ccb6a-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ccb6a-131">Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ccb6a-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ccb6a-132">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ccb6a-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ccb6a-133">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="ccb6a-133">Formatting Types</span></span>](../../../../docs/standard/base-types/formatting-types.md)
