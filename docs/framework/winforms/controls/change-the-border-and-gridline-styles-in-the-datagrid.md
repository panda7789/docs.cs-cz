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
ms.openlocfilehash: ebeca5f933eac4da2bf3d4f300866fd2ff52b32a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917676"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="dba00-102">Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="dba00-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="dba00-103"><xref:System.Windows.Forms.DataGridView> Pomocí ovládacího prvku můžete přizpůsobit vzhled ohraničení a mřížky ovládacího prvku pro zlepšení uživatelského prostředí.</span><span class="sxs-lookup"><span data-stu-id="dba00-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="dba00-104">Kromě stylů ohraničení buněk v ovládacím prvku můžete měnit barvu mřížky a styl ohraničení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dba00-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="dba00-105">Pro obyčejné buňky, buňky záhlaví řádku a buňky záhlaví sloupce můžete také použít jiné styly ohraničení buňky.</span><span class="sxs-lookup"><span data-stu-id="dba00-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dba00-106">Barva mřížky se používá pouze s <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single> <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> hodnotami <xref:System.Windows.Forms.DataGridViewCellBorderStyle> , <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>a výčtů a <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> hodnotou <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="dba00-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="dba00-107">Ostatní hodnoty těchto výčtů používají barvy určené operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="dba00-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="dba00-108">Kromě toho, pokud jsou vizuální styly povoleny v systému Windows XP a řada Windows Server 2003 pomocí <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody <xref:System.Windows.Forms.DataGridView.GridColor%2A> , není použita hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dba00-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="dba00-109">Chcete-li změnit barvu mřížky programově</span><span class="sxs-lookup"><span data-stu-id="dba00-109">To change the gridline color programmatically</span></span>  
  
- <span data-ttu-id="dba00-110"><xref:System.Windows.Forms.DataGridView.GridColor%2A> Nastavte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dba00-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="dba00-111">Změna stylu ohraničení celého ovládacího prvku DataGridView prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="dba00-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
- <span data-ttu-id="dba00-112">Nastavte vlastnost na jednu z hodnot <xref:System.Windows.Forms.BorderStyle> výčtu. <xref:System.Windows.Forms.DataGridView.BorderStyle%2A></span><span class="sxs-lookup"><span data-stu-id="dba00-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="dba00-113">Chcete-li změnit styly ohraničení pro buňky DataGridView programově</span><span class="sxs-lookup"><span data-stu-id="dba00-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
- <span data-ttu-id="dba00-114">Nastavte vlastnosti <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>a <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> .</span><span class="sxs-lookup"><span data-stu-id="dba00-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="dba00-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="dba00-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dba00-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="dba00-116">Compiling the Code</span></span>  
 <span data-ttu-id="dba00-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="dba00-117">This example requires:</span></span>  
  
- <span data-ttu-id="dba00-118">Ovládací prvek s `dataGridView1`názvem. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="dba00-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="dba00-119">Odkazy na <xref:System?displayProperty=nameWithType>sestavení, <xref:System.Windows.Forms?displayProperty=nameWithType>a. <xref:System.Drawing?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="dba00-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba00-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dba00-120">See also</span></span>

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [<span data-ttu-id="dba00-121">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="dba00-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
