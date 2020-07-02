---
title: Formátování dat v ovládacím prvku DataGridView
description: Naučte se formátovat hodnoty buněk pomocí model Windows Forms vlastnosti DefaultCellStyle ovládacího prvku DataGridView a specifických sloupců v ovládacím prvku.
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
ms.openlocfilehash: d6105c1d1120876f854332e7a10106cc1caf6276
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622806"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6a28f-103">Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6a28f-103">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6a28f-104">Následující postupy ukazují základní formátování hodnot buňky pomocí <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastnosti <xref:System.Windows.Forms.DataGridView> ovládacího prvku a specifických sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="6a28f-104">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="6a28f-105">Informace o pokročilých formátech dat naleznete [v tématu How to: Customizing Data Formatting in model Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6a28f-105">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="6a28f-106">Formátování hodnot měny a data</span><span class="sxs-lookup"><span data-stu-id="6a28f-106">To format currency and date values</span></span>  
  
- <span data-ttu-id="6a28f-107">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> .</span><span class="sxs-lookup"><span data-stu-id="6a28f-107">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="6a28f-108">Následující příklad kódu nastaví formát pro konkrétní sloupce pomocí <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnosti sloupců.</span><span class="sxs-lookup"><span data-stu-id="6a28f-108">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="6a28f-109">Hodnoty ve `UnitPrice` sloupci se zobrazí v aktuálním formátu měny specifické jazykové verze a záporné hodnoty jsou obklopeny závorkami.</span><span class="sxs-lookup"><span data-stu-id="6a28f-109">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="6a28f-110">Hodnoty ve `ShipDate` sloupci se zobrazí v aktuálním formátu krátkého data specifického pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="6a28f-110">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="6a28f-111">Další informace o <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> hodnotách naleznete v tématu [Formatting Types](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="6a28f-111">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="6a28f-112">Přizpůsobení zobrazení hodnot databáze s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="6a28f-112">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="6a28f-113">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> .</span><span class="sxs-lookup"><span data-stu-id="6a28f-113">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="6a28f-114">Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost k zobrazení "bez zadání" ve všech buňkách, které obsahují hodnoty rovny <xref:System.DBNull.Value?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6a28f-114">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="6a28f-115">Povolení WordWrap v textových buňkách</span><span class="sxs-lookup"><span data-stu-id="6a28f-115">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="6a28f-116">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> na jednu z <xref:System.Windows.Forms.DataGridViewTriState> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="6a28f-116">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="6a28f-117">Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost k nastavení režimu zalamování pro celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="6a28f-117">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="6a28f-118">Určení zarovnání textu buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="6a28f-118">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="6a28f-119">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> na jednu z <xref:System.Windows.Forms.DataGridViewContentAlignment> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="6a28f-119">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="6a28f-120">Následující příklad kódu nastaví zarovnání pro konkrétní sloupec pomocí <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnosti sloupce.</span><span class="sxs-lookup"><span data-stu-id="6a28f-120">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="6a28f-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a28f-121">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6a28f-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6a28f-122">Compiling the Code</span></span>  
 <span data-ttu-id="6a28f-123">Tyto příklady vyžadují:</span><span class="sxs-lookup"><span data-stu-id="6a28f-123">These examples require:</span></span>  
  
- <span data-ttu-id="6a28f-124"><xref:System.Windows.Forms.DataGridView>Ovládací prvek s názvem, `dataGridView1` který obsahuje sloupec s názvem `UnitPrice` , sloupec s názvem `ShipDate` a sloupec s názvem `CustomerName` .</span><span class="sxs-lookup"><span data-stu-id="6a28f-124">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="6a28f-125">Odkazy na <xref:System?displayProperty=nameWithType> sestavení, <xref:System.Drawing?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6a28f-125">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6a28f-126">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6a28f-126">Robust Programming</span></span>  
 <span data-ttu-id="6a28f-127">Pro zajištění maximální škálovatelnosti byste měli sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objekty napříč více řádky, sloupci nebo buňkami, které používají stejné styly, nikoli nastavovat vlastnosti stylu pro každý prvek samostatně.</span><span class="sxs-lookup"><span data-stu-id="6a28f-127">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="6a28f-128">Další informace najdete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6a28f-128">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a28f-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a28f-129">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="6a28f-130">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6a28f-130">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6a28f-131">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6a28f-131">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6a28f-132">Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6a28f-132">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6a28f-133">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6a28f-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6a28f-134">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="6a28f-134">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
