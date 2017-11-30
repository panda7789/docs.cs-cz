---
title: "Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView"
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
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb1c15be20775903a6fb7674660c552c464daab1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="37c8b-102">Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="37c8b-102">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="37c8b-103">Můžete určit vzhled buněk v rámci <xref:System.Windows.Forms.DataGridView> ovládací prvek pro nastavení vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> třídy.</span><span class="sxs-lookup"><span data-stu-id="37c8b-103">You can specify the visual appearance of cells within a <xref:System.Windows.Forms.DataGridView> control by setting properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span> <span data-ttu-id="37c8b-104">Instance této třídy můžete načíst z různé vlastnosti <xref:System.Windows.Forms.DataGridView> můžete vytvořit instanci třídy a jejich doprovodné třídy nebo můžete <xref:System.Windows.Forms.DataGridViewCellStyle> objekty pro přiřazení do těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="37c8b-104">You can retrieve instances of this class from various properties of the <xref:System.Windows.Forms.DataGridView> class and its companion classes, or you can instantiate <xref:System.Windows.Forms.DataGridViewCellStyle> objects for assignment to these properties.</span></span>  
  
 <span data-ttu-id="37c8b-105">Následující postupy ukazují základní přizpůsobení pomocí vzhledu buněk <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="37c8b-105">The following procedures demonstrate basic customization of cell appearance using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property.</span></span> <span data-ttu-id="37c8b-106">Všechny buňky v ovládacím prvku dědí styly zadaná pomocí této vlastnosti přepsána na sloupce, řádku nebo na úrovni buněk.</span><span class="sxs-lookup"><span data-stu-id="37c8b-106">Every cell in the control inherits the styles specified through this property unless they are overridden at the column, row, or cell level.</span></span> <span data-ttu-id="37c8b-107">Příklad styl dědičnosti, naleznete v části [postupy: nastavení výchozí styly buňky pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="37c8b-107">For an example of style inheritance, see [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="37c8b-108">Informace o použití Další <xref:System.Windows.Forms.DataGridViewCellStyle> třídy, najdete v tématech uvedených v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="37c8b-108">For information about additional uses of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, see the topics listed in the See Also section.</span></span>  
  
 <span data-ttu-id="37c8b-109">Rozsáhlá podpora pro tuto úlohu v sadě Visual Studio není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="37c8b-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="37c8b-110">Viz také [postup: nastavte výchozí styly buňky a Data formátů Windows Forms DataGridView – ovládací prvek s využitím návrháře](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="37c8b-110">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span></span>  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a><span data-ttu-id="37c8b-111">Chcete-li určit písmo použité buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="37c8b-111">To specify the font used by DataGridView cells</span></span>  
  
-   <span data-ttu-id="37c8b-112">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="37c8b-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="37c8b-113">Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost nastavení písma pro celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="37c8b-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the font for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a><span data-ttu-id="37c8b-114">Chcete-li určit barev popředí a na pozadí buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="37c8b-114">To specify the foreground and background colors of DataGridView cells</span></span>  
  
-   <span data-ttu-id="37c8b-115">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="37c8b-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="37c8b-116">Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost nastavující tyto styly pro celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="37c8b-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a><span data-ttu-id="37c8b-117">Zadat obecné barvy vybraných buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="37c8b-117">To specify the foreground and background colors of selected DataGridView cells</span></span>  
  
-   <span data-ttu-id="37c8b-118">Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="37c8b-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="37c8b-119">Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost nastavující tyto styly pro celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="37c8b-119">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a><span data-ttu-id="37c8b-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="37c8b-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37c8b-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="37c8b-121">Compiling the Code</span></span>  
 <span data-ttu-id="37c8b-122">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="37c8b-122">This example requires:</span></span>  
  
-   <span data-ttu-id="37c8b-123">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="37c8b-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="37c8b-124">Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="37c8b-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="37c8b-125">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="37c8b-125">Robust Programming</span></span>  
 <span data-ttu-id="37c8b-126">Pro maximální škálovatelnost, by měly sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více řádků, sloupců nebo buněk, které používají stejné styly, nikoli nastavení vlastnosti stylu pro každý prvek samostatně.</span><span class="sxs-lookup"><span data-stu-id="37c8b-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="37c8b-127">Další informace najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="37c8b-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c8b-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="37c8b-128">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="37c8b-129">Základní formátování a styly v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="37c8b-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="37c8b-130">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="37c8b-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
