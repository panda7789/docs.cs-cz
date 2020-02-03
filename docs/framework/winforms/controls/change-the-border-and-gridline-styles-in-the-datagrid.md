---
title: Změna stylů ohraničení a mřížky v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: 918102a87ee29a3d3b78d6e6eedce57237135a51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744695"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a54ec-102">Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a54ec-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a54ec-103">Pomocí ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit vzhled ohraničení a mřížky ovládacího prvku pro zlepšení uživatelského prostředí.</span><span class="sxs-lookup"><span data-stu-id="a54ec-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="a54ec-104">Kromě stylů ohraničení buněk v ovládacím prvku můžete měnit barvu mřížky a styl ohraničení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a54ec-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="a54ec-105">Pro obyčejné buňky, buňky záhlaví řádku a buňky záhlaví sloupce můžete také použít jiné styly ohraničení buňky.</span><span class="sxs-lookup"><span data-stu-id="a54ec-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a54ec-106">Barva mřížky se používá pouze v hodnotách <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>a <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> hodnoty výčtu <xref:System.Windows.Forms.DataGridViewCellBorderStyle> a <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> hodnota výčtu <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="a54ec-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="a54ec-107">Ostatní hodnoty těchto výčtů používají barvy určené operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="a54ec-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="a54ec-108">Kromě toho, pokud jsou vizuální styly povoleny v systému Windows XP a v rodině systému Windows Server 2003 pomocí metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>, není použita hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.GridColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="a54ec-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="a54ec-109">Chcete-li změnit barvu mřížky programově</span><span class="sxs-lookup"><span data-stu-id="a54ec-109">To change the gridline color programmatically</span></span>  
  
- <span data-ttu-id="a54ec-110">Nastavte vlastnost <xref:System.Windows.Forms.DataGridView.GridColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="a54ec-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="a54ec-111">Změna stylu ohraničení celého ovládacího prvku DataGridView prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="a54ec-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
- <span data-ttu-id="a54ec-112">Vlastnost <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> nastavte na jednu z hodnot výčtu <xref:System.Windows.Forms.BorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="a54ec-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="a54ec-113">Chcete-li změnit styly ohraničení pro buňky DataGridView programově</span><span class="sxs-lookup"><span data-stu-id="a54ec-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
- <span data-ttu-id="a54ec-114">Nastavte vlastnosti <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>a <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="a54ec-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="a54ec-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a54ec-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a54ec-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a54ec-116">Compiling the Code</span></span>  
 <span data-ttu-id="a54ec-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a54ec-117">This example requires:</span></span>  
  
- <span data-ttu-id="a54ec-118"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="a54ec-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="a54ec-119">Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>a <xref:System.Drawing?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a54ec-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a54ec-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a54ec-120">See also</span></span>

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [<span data-ttu-id="a54ec-121">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a54ec-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
