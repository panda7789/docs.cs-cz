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
ms.openlocfilehash: 7b2fc4e15ac1728faefebc932bc4d125a6902168
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56663948"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="d51ff-102">Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d51ff-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d51ff-103">S <xref:System.Windows.Forms.DataGridView> ovládacího prvku, můžete zadat výchozích stylů buňky pro celý ovládací prvek a pro určité sloupce a řádky.</span><span class="sxs-lookup"><span data-stu-id="d51ff-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="d51ff-104">Tyto výchozí hodnoty vyfiltrovat z úrovně ovládacího prvku na úrovni sloupce pak na úrovni řádků a pak na úrovni buněk.</span><span class="sxs-lookup"><span data-stu-id="d51ff-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="d51ff-105">Pokud konkrétní <xref:System.Windows.Forms.DataGridViewCellStyle> vlastnost není nastavená na úrovni buňky, bude použito výchozí nastavení vlastnosti na úrovni řádků.</span><span class="sxs-lookup"><span data-stu-id="d51ff-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="d51ff-106">Pokud není vlastnost také nastavit na úrovni řádků, sloupců ve výchozím nastavení se používá.</span><span class="sxs-lookup"><span data-stu-id="d51ff-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="d51ff-107">Nakonec pokud není vlastnost také nastavit na úrovni sloupce, výchozí <xref:System.Windows.Forms.DataGridView> nastavení se používá.</span><span class="sxs-lookup"><span data-stu-id="d51ff-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="d51ff-108">Při tomto nastavení se vyhnete nutnosti mít duplicitní nastavení vlastnosti na více úrovních.</span><span class="sxs-lookup"><span data-stu-id="d51ff-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="d51ff-109">Na každé úrovni zadejte jednoduše styly, které se liší od úrovně nad ním.</span><span class="sxs-lookup"><span data-stu-id="d51ff-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="d51ff-110">Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d51ff-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="d51ff-111">Není k dispozici rozsáhlou podporu pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d51ff-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="d51ff-112">Viz také [jak: Nastavení výchozích stylů buňky a datových formátů pro Windows Forms DataGridView pomocí návrháře](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="d51ff-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="d51ff-113">Nastavení výchozích stylů buňky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="d51ff-113">To set the default cell styles programmatically</span></span>  
  
1.  <span data-ttu-id="d51ff-114">Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> získat pomocí <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d51ff-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  <span data-ttu-id="d51ff-115">Vytváření a inicializace nového <xref:System.Windows.Forms.DataGridViewCellStyle> objekty používají více řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="d51ff-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  <span data-ttu-id="d51ff-116">Nastavte `DefaultCellStyle` vlastnost konkrétní řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="d51ff-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="d51ff-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="d51ff-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d51ff-118">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d51ff-118">Compiling the Code</span></span>  
 <span data-ttu-id="d51ff-119">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="d51ff-119">This example requires:</span></span>  
  
-   <span data-ttu-id="d51ff-120">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="d51ff-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="d51ff-121">Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="d51ff-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d51ff-122">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d51ff-122">Robust Programming</span></span>  
 <span data-ttu-id="d51ff-123">Pro dosažení maximální škálovatelnosti při práci s velmi velkými datovými sadami, by měly sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více řádky, sloupce nebo buňky, které použijte stejné styly, nikoli samostatně nastavte vlastnosti stylu pro jednotlivé prvky.</span><span class="sxs-lookup"><span data-stu-id="d51ff-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="d51ff-124">Kromě toho by měl vytvořit sdílené řádky a k nim přistupovat pomocí <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d51ff-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d51ff-125">Další informace najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d51ff-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51ff-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d51ff-126">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d51ff-127">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d51ff-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d51ff-128">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d51ff-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d51ff-129">Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d51ff-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d51ff-130">Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d51ff-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
