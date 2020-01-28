---
title: Přizpůsobení vzhledu buněk v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 754932427a365a7b032c1ac9627d3237d1f7d0c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744050"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9e0dd-102">Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9e0dd-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9e0dd-103">Můžete přizpůsobit vzhled libovolné buňky zpracováním události <xref:System.Windows.Forms.DataGridView.CellPainting> ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="9e0dd-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="9e0dd-104"><xref:System.Drawing.Graphics> ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete extrahovat z vlastnosti <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="9e0dd-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="9e0dd-105">V tomto <xref:System.Drawing.Graphics>můžete ovlivnit vzhled celého ovládacího prvku <xref:System.Windows.Forms.DataGridView>, ale obvykle budete chtít mít vliv pouze na vzhled buňky, která je právě vykreslena.</span><span class="sxs-lookup"><span data-stu-id="9e0dd-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="9e0dd-106">Vlastnost <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> umožňuje omezit operace malování na buňku, která je právě vykreslena.</span><span class="sxs-lookup"><span data-stu-id="9e0dd-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="9e0dd-107">V následujícím příkladu kódu budete malovat všechny buňky ve sloupci `ContactName` pomocí barevného schématu ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="9e0dd-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="9e0dd-108">Textový obsah každé buňky se vykresluje <xref:System.Drawing.Color.Crimson%2A>a vsazený obdélník se vykreslí stejnou barvou jako vlastnost <xref:System.Windows.Forms.DataGridView.GridColor%2A> ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="9e0dd-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e0dd-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e0dd-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9e0dd-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9e0dd-110">Compiling the Code</span></span>  
 <span data-ttu-id="9e0dd-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9e0dd-111">This example requires:</span></span>  
  
- <span data-ttu-id="9e0dd-112"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` se sloupcem `ContactName`, jako je například ten v tabulce Customers v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="9e0dd-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
- <span data-ttu-id="9e0dd-113">Odkazy na sestavení System, System. Windows. Forms a System. Drawing.</span><span class="sxs-lookup"><span data-stu-id="9e0dd-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0dd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e0dd-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [<span data-ttu-id="9e0dd-115">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9e0dd-115">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
