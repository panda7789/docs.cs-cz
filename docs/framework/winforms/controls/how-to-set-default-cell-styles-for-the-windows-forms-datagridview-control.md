---
title: Nastavení výchozích stylů buňky pro ovládací prvek DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 6b2d7de671e48ae8f55987c262e15717138b3fb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744865"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="1ebd4-102">Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ebd4-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1ebd4-103">Pomocí ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete určit výchozí styly buněk pro celý ovládací prvek a pro konkrétní sloupce a řádky.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="1ebd4-104">Tyto výchozí hodnoty se filtrují z úrovně ovládacího prvku na úroveň sloupce a pak na úroveň řádku a na úroveň buňky.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="1ebd4-105">Pokud není nastavená určitá vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> na úrovni buňky, použije se výchozí nastavení vlastnosti na úrovni řádku.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="1ebd4-106">Pokud vlastnost není nastavena i na úrovni řádku, použije se výchozí nastavení sloupce.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="1ebd4-107">Nakonec, pokud vlastnost není nastavena také na úrovni sloupce, je použita výchozí hodnota <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="1ebd4-108">Pomocí tohoto nastavení můžete zabránit duplikaci nastavení vlastností na více úrovních.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="1ebd4-109">Na každé úrovni jednoduše určete styly, které se liší od úrovní nad ní.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="1ebd4-110">Další informace naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1ebd4-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="1ebd4-111">Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="1ebd4-112">Viz také [Postupy: nastavení výchozích stylů buňky a datových formátů pro ovládací prvek DataGridView model Windows Forms pomocí návrháře](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="1ebd4-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="1ebd4-113">Chcete-li nastavit výchozí styly buněk programově</span><span class="sxs-lookup"><span data-stu-id="1ebd4-113">To set the default cell styles programmatically</span></span>  
  
1. <span data-ttu-id="1ebd4-114">Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> načtené prostřednictvím vlastnosti <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2. <span data-ttu-id="1ebd4-115">Umožňuje vytvořit a inicializovat nové objekty <xref:System.Windows.Forms.DataGridViewCellStyle> pro použití více řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3. <span data-ttu-id="1ebd4-116">Nastavte vlastnost `DefaultCellStyle` pro určité řádky a sloupce.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="1ebd4-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ebd4-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1ebd4-118">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1ebd4-118">Compiling the Code</span></span>  
 <span data-ttu-id="1ebd4-119">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1ebd4-119">This example requires:</span></span>  
  
- <span data-ttu-id="1ebd4-120"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="1ebd4-121">Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>a <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1ebd4-122">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1ebd4-122">Robust Programming</span></span>  
 <span data-ttu-id="1ebd4-123">Chcete-li dosáhnout maximální škálovatelnosti při práci s velmi velkými datovými sadami, měli byste sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objekty napříč více řádky, sloupci nebo buňkami, které používají stejné styly, nikoli nastavit vlastnosti stylu pro jednotlivé prvky samostatně.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="1ebd4-124">Kromě toho byste měli vytvořit sdílené řádky a přistupovat k nim pomocí vlastnosti <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1ebd4-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1ebd4-125">Další informace najdete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1ebd4-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ebd4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ebd4-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1ebd4-127">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ebd4-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1ebd4-128">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ebd4-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1ebd4-129">Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ebd4-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1ebd4-130">Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ebd4-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
