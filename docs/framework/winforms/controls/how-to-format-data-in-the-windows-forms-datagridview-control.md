---
title: Formátování dat v ovládacím prvku DataGridView
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
ms.openlocfilehash: 9ee2869cf4085b5acfdf1f8c440151be506dbe3e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736785"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6692a-102">Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6692a-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6692a-103">Následující postupy ukazují základní formátování hodnot buňky pomocí vlastnosti <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> ovládacího prvku <xref:System.Windows.Forms.DataGridView> a specifických sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="6692a-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="6692a-104">Informace o pokročilých formátech dat naleznete [v tématu How to: Customizing Data Formatting in model Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6692a-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="6692a-105">Formátování hodnot měny a data</span><span class="sxs-lookup"><span data-stu-id="6692a-105">To format currency and date values</span></span>  
  
- <span data-ttu-id="6692a-106">Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="6692a-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="6692a-107">Následující příklad kódu nastaví formát pro konkrétní sloupce pomocí vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> sloupců.</span><span class="sxs-lookup"><span data-stu-id="6692a-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="6692a-108">Hodnoty ve sloupci `UnitPrice` se zobrazí v aktuálním formátu měny specifickém pro jazykovou verzi, přičemž záporné hodnoty jsou obklopeny závorkami.</span><span class="sxs-lookup"><span data-stu-id="6692a-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="6692a-109">Hodnoty ve sloupci `ShipDate` se zobrazí v aktuálním formátu krátkého data specifického pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="6692a-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="6692a-110">Další informace o <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> hodnotách naleznete v tématu [Formatting Types](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="6692a-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="6692a-111">Přizpůsobení zobrazení hodnot databáze s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="6692a-111">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="6692a-112">Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="6692a-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="6692a-113">Následující příklad kódu používá vlastnost <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> k zobrazení "bez zadání" ve všech buňkách, které obsahují hodnoty rovné <xref:System.DBNull.Value?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6692a-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="6692a-114">Povolení WordWrap v textových buňkách</span><span class="sxs-lookup"><span data-stu-id="6692a-114">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="6692a-115">Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> <xref:System.Windows.Forms.DataGridViewCellStyle> na jednu z hodnot výčtu <xref:System.Windows.Forms.DataGridViewTriState>.</span><span class="sxs-lookup"><span data-stu-id="6692a-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="6692a-116">Následující příklad kódu používá vlastnost <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> k nastavení režimu zalamování pro celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="6692a-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="6692a-117">Určení zarovnání textu buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="6692a-117">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="6692a-118">Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> <xref:System.Windows.Forms.DataGridViewCellStyle> na jednu z hodnot výčtu <xref:System.Windows.Forms.DataGridViewContentAlignment>.</span><span class="sxs-lookup"><span data-stu-id="6692a-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="6692a-119">Následující příklad kódu nastaví zarovnání pro určitý sloupec pomocí vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> sloupce.</span><span class="sxs-lookup"><span data-stu-id="6692a-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="6692a-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="6692a-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6692a-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6692a-121">Compiling the Code</span></span>  
 <span data-ttu-id="6692a-122">Tyto příklady vyžadují:</span><span class="sxs-lookup"><span data-stu-id="6692a-122">These examples require:</span></span>  
  
- <span data-ttu-id="6692a-123"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` obsahující sloupec s názvem `UnitPrice`, sloupec s názvem `ShipDate`a sloupec s názvem `CustomerName`.</span><span class="sxs-lookup"><span data-stu-id="6692a-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="6692a-124">Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>a <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6692a-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6692a-125">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6692a-125">Robust Programming</span></span>  
 <span data-ttu-id="6692a-126">Pro maximální škálovatelnost byste měli sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objekty napříč více řádky, sloupci nebo buňkami, které používají stejné styly namísto nastavení vlastností stylu pro každý prvek samostatně.</span><span class="sxs-lookup"><span data-stu-id="6692a-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="6692a-127">Další informace najdete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6692a-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6692a-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6692a-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="6692a-129">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6692a-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6692a-130">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6692a-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6692a-131">Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6692a-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6692a-132">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6692a-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6692a-133">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="6692a-133">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
