---
title: 'Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: d24adb98c339f911d6bea0312bce4d4b4f198a61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939006"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="55117-102">Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="55117-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="55117-103">S <xref:System.Windows.Forms.DataGridView> ovládacího prvku, lze přizpůsobit vzhled ohraničení a mřížky vylepšit uživatelské prostředí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="55117-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="55117-104">Můžete změnit barvu mřížky a styl ohraničení ovládacího prvku kromě styly ohraničení buněk v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="55117-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="55117-105">Můžete také použít jinou buňku styly ohraničení pro běžné buněk, buněk záhlaví řádku a buňky záhlaví sloupce.</span><span class="sxs-lookup"><span data-stu-id="55117-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55117-106">Barvu mřížky se používá jenom s <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, a <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> hodnoty <xref:System.Windows.Forms.DataGridViewCellBorderStyle> výčet a <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> hodnotu <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="55117-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="55117-107">Ostatní hodnoty těchto výčty používat barvy definované v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="55117-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="55117-108">Kromě toho, když je vizuální styly povoleno na Windows XP a Windows Server 2003 až <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody, <xref:System.Windows.Forms.DataGridView.GridColor%2A> hodnota vlastnosti se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="55117-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="55117-109">Chcete-li změnit barvu mřížky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="55117-109">To change the gridline color programmatically</span></span>  
  
- <span data-ttu-id="55117-110">Nastavte <xref:System.Windows.Forms.DataGridView.GridColor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="55117-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="55117-111">Chcete-li změnit styl ohraničení celý ovládací prvek DataGridView prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="55117-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
- <span data-ttu-id="55117-112">Nastavte <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> vlastnost na jednu z <xref:System.Windows.Forms.BorderStyle> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="55117-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="55117-113">Změna stylů ohraničení buněk DataGridView prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="55117-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
- <span data-ttu-id="55117-114">Nastavte <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, a <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="55117-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="55117-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="55117-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="55117-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="55117-116">Compiling the Code</span></span>  
 <span data-ttu-id="55117-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="55117-117">This example requires:</span></span>  
  
- <span data-ttu-id="55117-118">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="55117-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="55117-119">Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Drawing?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="55117-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55117-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55117-120">See also</span></span>

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [<span data-ttu-id="55117-121">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="55117-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
