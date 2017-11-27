---
title: "Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView"
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
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a31e8eb02949c0f6db487e3cd1a6976f2ed37222
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="e9bb1-102">Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e9bb1-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e9bb1-103">Tabulková data se často zobrazí uživatelům ve formátu, účetní knihy, kde střídavých řádků mají různých barev pozadí.</span><span class="sxs-lookup"><span data-stu-id="e9bb1-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="e9bb1-104">Tento formát usnadňuje uživatelům říct buněk, které jsou v jednotlivých řádcích, zejména s wide tabulky, které mají mnoho sloupců.</span><span class="sxs-lookup"><span data-stu-id="e9bb1-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="e9bb1-105">Pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete zadat informace o dokončení stylu střídavých řádků.</span><span class="sxs-lookup"><span data-stu-id="e9bb1-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="e9bb1-106">Díky této může použít vlastnosti stylu jako barvu popředí a písma, kromě barvu pozadí k odlišení střídavých řádků.</span><span class="sxs-lookup"><span data-stu-id="e9bb1-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="e9bb1-107">Není poskytována podpora pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9bb1-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="e9bb1-108">Viz také [postupy: nastavení střídavých řádků styly Windows Forms DataGridView – ovládací prvek s využitím návrháře](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e9bb1-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="e9bb1-109">Nastavení stylů střídavých řádků prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="e9bb1-109">To set alternating row styles programmatically</span></span>  
  
-   <span data-ttu-id="e9bb1-110">Nastavit vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> objektů vrácený <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> vlastnosti <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="e9bb1-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  <span data-ttu-id="e9bb1-111">Styly definované, pomocí <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> vlastnosti přepsání styly definované ve sloupci a <xref:System.Windows.Forms.DataGridView> úrovni, ale jsou přepsány styly nastavit na úrovni jednotlivých řádku a buňky.</span><span class="sxs-lookup"><span data-stu-id="e9bb1-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="e9bb1-112">Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e9bb1-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e9bb1-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e9bb1-113">Compiling the Code</span></span>  
 <span data-ttu-id="e9bb1-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e9bb1-114">This example requires:</span></span>  
  
-   <span data-ttu-id="e9bb1-115">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="e9bb1-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="e9bb1-116">Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9bb1-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e9bb1-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="e9bb1-117">Robust Programming</span></span>  
 <span data-ttu-id="e9bb1-118">Pro maximální škálovatelnost, by měly sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více řádků, sloupců nebo buněk, které používají stejné styly, nikoli nastavení vlastnosti stylu pro každý prvek samostatně.</span><span class="sxs-lookup"><span data-stu-id="e9bb1-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="e9bb1-119">Další informace najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e9bb1-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9bb1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9bb1-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="e9bb1-121">Základní formátování a styly v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="e9bb1-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e9bb1-122">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e9bb1-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e9bb1-123">Osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e9bb1-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e9bb1-124">Postupy: nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e9bb1-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
