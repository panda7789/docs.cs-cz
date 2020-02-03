---
title: Nastavení stylů písma a barev v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
ms.openlocfilehash: f1ee9131cfc0b28a5f6263dcd6254d27a092cc62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746755"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e4edb-102">Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e4edb-102">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e4edb-103">Můžete určit vizuální vzhled buněk v ovládacím prvku <xref:System.Windows.Forms.DataGridView> nastavením vlastností <xref:System.Windows.Forms.DataGridViewCellStyle> třídy.</span><span class="sxs-lookup"><span data-stu-id="e4edb-103">You can specify the visual appearance of cells within a <xref:System.Windows.Forms.DataGridView> control by setting properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span> <span data-ttu-id="e4edb-104">Můžete načíst instance této třídy z různých vlastností třídy <xref:System.Windows.Forms.DataGridView> a jejích doprovodných tříd, nebo můžete vytvořit instanci <xref:System.Windows.Forms.DataGridViewCellStyle> objektů pro přiřazení k těmto vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="e4edb-104">You can retrieve instances of this class from various properties of the <xref:System.Windows.Forms.DataGridView> class and its companion classes, or you can instantiate <xref:System.Windows.Forms.DataGridViewCellStyle> objects for assignment to these properties.</span></span>  
  
 <span data-ttu-id="e4edb-105">Následující postupy ukazují základní přizpůsobení vzhledu buňky pomocí vlastnosti <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4edb-105">The following procedures demonstrate basic customization of cell appearance using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property.</span></span> <span data-ttu-id="e4edb-106">Každá buňka v ovládacím prvku dědí styly zadané přes tuto vlastnost, pokud nejsou přepsány na úrovni sloupce, řádku nebo buňky.</span><span class="sxs-lookup"><span data-stu-id="e4edb-106">Every cell in the control inherits the styles specified through this property unless they are overridden at the column, row, or cell level.</span></span> <span data-ttu-id="e4edb-107">Příklad dědičnosti stylu naleznete v tématu [How to: set pro výchozí styly buněk pro ovládací prvek DataGridView model Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e4edb-107">For an example of style inheritance, see [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="e4edb-108">Informace o dalších použitích třídy <xref:System.Windows.Forms.DataGridViewCellStyle> naleznete v tématech uvedených v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="e4edb-108">For information about additional uses of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, see the topics listed in the See Also section.</span></span>  
  
 <span data-ttu-id="e4edb-109">Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e4edb-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="e4edb-110">Viz také [Postupy: nastavení výchozích stylů buňky a datových formátů pro ovládací prvek DataGridView model Windows Forms pomocí návrháře](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="e4edb-110">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a><span data-ttu-id="e4edb-111">Určení písma používaného buňkami DataGridView</span><span class="sxs-lookup"><span data-stu-id="e4edb-111">To specify the font used by DataGridView cells</span></span>  
  
- <span data-ttu-id="e4edb-112">Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="e4edb-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="e4edb-113">Následující příklad kódu používá vlastnost <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> k nastavení písma pro celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e4edb-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the font for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a><span data-ttu-id="e4edb-114">Určení barvy popředí a pozadí buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="e4edb-114">To specify the foreground and background colors of DataGridView cells</span></span>  
  
- <span data-ttu-id="e4edb-115">Nastavení vlastností <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="e4edb-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="e4edb-116">Následující příklad kódu používá vlastnost <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> k nastavení těchto stylů pro celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e4edb-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a><span data-ttu-id="e4edb-117">Chcete-li určit barvy popředí a pozadí vybraných buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="e4edb-117">To specify the foreground and background colors of selected DataGridView cells</span></span>  
  
- <span data-ttu-id="e4edb-118">Nastavení vlastností <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="e4edb-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="e4edb-119">Následující příklad kódu používá vlastnost <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> k nastavení těchto stylů pro celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e4edb-119">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a><span data-ttu-id="e4edb-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4edb-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4edb-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e4edb-121">Compiling the Code</span></span>  
 <span data-ttu-id="e4edb-122">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e4edb-122">This example requires:</span></span>  
  
- <span data-ttu-id="e4edb-123"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="e4edb-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="e4edb-124">Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>a <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e4edb-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e4edb-125">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="e4edb-125">Robust Programming</span></span>  
 <span data-ttu-id="e4edb-126">Pro zajištění maximální škálovatelnosti byste měli sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objekty napříč více řádky, sloupci nebo buňkami, které používají stejné styly, nikoli nastavovat vlastnosti stylu pro každý prvek samostatně.</span><span class="sxs-lookup"><span data-stu-id="e4edb-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="e4edb-127">Další informace najdete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e4edb-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4edb-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4edb-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="e4edb-129">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e4edb-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e4edb-130">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e4edb-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
