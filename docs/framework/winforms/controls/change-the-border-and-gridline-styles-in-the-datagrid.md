---
title: "Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView"
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
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ebe73e0c29a211e3319998ef7acd14e78e4eb14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="065e1-102">Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="065e1-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="065e1-103">Pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete přizpůsobit vzhled ovládacího prvku ohraničení a mřížky ke zlepšení činnost koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="065e1-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="065e1-104">Můžete upravit barvy čar mřížky a styl ohraničení ovládacího prvku kromě styly ohraničení buněk v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="065e1-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="065e1-105">Můžete také použít jinou buňku styly ohraničení pro běžné buněk, buňky záhlaví řádků a buňky záhlaví sloupce.</span><span class="sxs-lookup"><span data-stu-id="065e1-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="065e1-106">Barva čar mřížky se používá jenom s <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, a <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> hodnoty <xref:System.Windows.Forms.DataGridViewCellBorderStyle> – výčet a <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> hodnotu <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> – výčet.</span><span class="sxs-lookup"><span data-stu-id="065e1-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="065e1-107">Ostatní hodnoty těchto výčty pomocí barvy definované v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="065e1-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="065e1-108">Kromě toho, když jsou vizuální styly povoleno na systémy Windows XP a řady Windows Server 2003 prostřednictvím <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody <xref:System.Windows.Forms.DataGridView.GridColor%2A> nepoužívá hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="065e1-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="065e1-109">Chcete-li změnit barvu čar mřížky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="065e1-109">To change the gridline color programmatically</span></span>  
  
-   <span data-ttu-id="065e1-110">Nastavte <xref:System.Windows.Forms.DataGridView.GridColor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="065e1-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="065e1-111">Chcete-li změnit styl ohraničení celý ovládací prvek DataGridView prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="065e1-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
-   <span data-ttu-id="065e1-112">Nastavte <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> vlastnost na jednu z <xref:System.Windows.Forms.BorderStyle> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="065e1-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="065e1-113">Chcete-li změnit styl buněk DataGridView prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="065e1-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
-   <span data-ttu-id="065e1-114">Nastavte <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, a <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="065e1-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="065e1-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="065e1-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="065e1-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="065e1-116">Compiling the Code</span></span>  
 <span data-ttu-id="065e1-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="065e1-117">This example requires:</span></span>  
  
-   <span data-ttu-id="065e1-118">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="065e1-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="065e1-119">Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Drawing?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="065e1-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065e1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="065e1-120">See Also</span></span>  
 <xref:System.Windows.Forms.BorderStyle>  
 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>  
 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>  
 [<span data-ttu-id="065e1-121">Základní formátování a styly v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="065e1-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
