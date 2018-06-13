---
title: 'Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: ed7ff720d8ef4aa2caa858ea61c4d38866cf50a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538677"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="7d67a-102">Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d67a-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7d67a-103">Pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete zadat výchozích stylů buňky pro celý ovládací prvek a pro určité sloupce a řádky.</span><span class="sxs-lookup"><span data-stu-id="7d67a-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="7d67a-104">Tyto výchozí hodnoty filtrovat dolů z úrovně řízení na úrovni sloupce, pak úroveň řádek, dále na úrovni buněk.</span><span class="sxs-lookup"><span data-stu-id="7d67a-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="7d67a-105">Pokud určitý <xref:System.Windows.Forms.DataGridViewCellStyle> na úrovni buněk není nastavena vlastnost, bude použita výchozí nastavení vlastnosti na úrovni řádků.</span><span class="sxs-lookup"><span data-stu-id="7d67a-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="7d67a-106">Pokud také není vlastnost nastavena na úrovni řádků, použije se výchozí nastavení sloupce.</span><span class="sxs-lookup"><span data-stu-id="7d67a-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="7d67a-107">Nakonec pokud není vlastnost také nastavena na úrovni sloupce, výchozí <xref:System.Windows.Forms.DataGridView> nastavení se používá.</span><span class="sxs-lookup"><span data-stu-id="7d67a-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="7d67a-108">Při tomto nastavení se můžete vyhnout nutnosti mít duplicitní hodnoty vlastností na více úrovních.</span><span class="sxs-lookup"><span data-stu-id="7d67a-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="7d67a-109">Na každé úrovni jednoduše zadejte stylů, které se liší od úrovně nad ním.</span><span class="sxs-lookup"><span data-stu-id="7d67a-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="7d67a-110">Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7d67a-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="7d67a-111">Rozsáhlá podpora pro tuto úlohu v sadě Visual Studio není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7d67a-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="7d67a-112">Viz také [postup: nastavte výchozí styly buňky a Data formátů Windows Forms DataGridView – ovládací prvek s využitím návrháře](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7d67a-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="7d67a-113">Nastavení výchozích stylů buňky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="7d67a-113">To set the default cell styles programmatically</span></span>  
  
1.  <span data-ttu-id="7d67a-114">Nastavit vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> načteny prostřednictvím <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d67a-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  <span data-ttu-id="7d67a-115">Vytvoření a inicializace nové <xref:System.Windows.Forms.DataGridViewCellStyle> objekty za účelem použití více řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="7d67a-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  <span data-ttu-id="7d67a-116">Nastavte `DefaultCellStyle` vlastnost konkrétní řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="7d67a-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="7d67a-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d67a-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7d67a-118">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7d67a-118">Compiling the Code</span></span>  
 <span data-ttu-id="7d67a-119">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7d67a-119">This example requires:</span></span>  
  
-   <span data-ttu-id="7d67a-120">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="7d67a-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="7d67a-121">Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d67a-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7d67a-122">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="7d67a-122">Robust Programming</span></span>  
 <span data-ttu-id="7d67a-123">K dosažení maximální škálovatelnost při práci s velmi velkých datových sad, by měly sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více řádků, sloupců nebo buněk, které použít stejné styly, nikoli samostatně nastavte vlastnosti stylu pro jednotlivé elementy.</span><span class="sxs-lookup"><span data-stu-id="7d67a-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="7d67a-124">Kromě toho by měl vytvořit sdílené řádky a přistupovat k nim pomocí <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d67a-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7d67a-125">Další informace najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7d67a-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d67a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d67a-126">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="7d67a-127">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d67a-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="7d67a-128">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d67a-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="7d67a-129">Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d67a-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="7d67a-130">Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7d67a-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
